<template>
  <el-select
    v-model="selectedOrgId"
    size="small"
    v-loading="dataListLoading"
    @change="selectAccount"
    filterable
  >
    <el-option v-for="(item,key) in accountList" :key="key" :label="item.orgName" :value="item.id"></el-option>
  </el-select>
</template>
<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      dataListLoading: false,
      accountList: {},
      selectedOrgId: "",
    };
  },
  mounted() {
    this.getDataList();
  },
  methods: {
    getDataList() {
      this.$http({
        url: this.$http.adornUrl("/apiauth/orglist"),
      }).then(({ data }) => {
        if (data.success) {
          this.accountList = data.data;
          this.selectAccount(sessionStorage.getItem("orgId"));
        } else {
          this.$message({
            type: "error",
            message: data.message,
          });
        }
      });
    },
    selectAccount(orgId) {
      if(!orgId || orgId==''){
        orgId = this.getFirst().id;
      }

      if (this.selectedOrgId != orgId) {
        this.selectedOrgId = orgId;
      }

      var oldOrgId = sessionStorage.getItem("orgId");
      if (oldOrgId != this.selectedOrgId) {
        sessionStorage.setItem("orgId", this.selectedOrgId);
        location.reload();
      }

    },
    
    getFirst() {
      for (var key in this.accountList) {
        return this.accountList[key];
      }
    },
  },
};
</script>