<template>
  <div class="layout">
    <iLayout>
      <iSider breakpoint="md" collapsible :collapsed-width="78" v-model="isCollapsed">
        <iMenu active-name="coder" theme="dark" width="auto" :class="menuitemClasses">
          <iMenuItem name="code">
            <router-link to="/coderManage">
              <iIcon type="laptop"></iIcon>
              <span>代码生成</span></router-link>
          </iMenuItem>
        </iMenu>
        <div slot="trigger"></div>
      </iSider>
      <iLayout>
        <iHeader class="layout-header-bar"></iHeader>
        <iContent :style="{margin: '5px', background: '#fff', minHeight: '220px'}">
          <iBreadcrumb :style="{margin: '10px 5px'}">
            <iBreadcrumbItem>首页</iBreadcrumbItem>
            <iBreadcrumbItem>开发辅助</iBreadcrumbItem>
            <iBreadcrumbItem>代码生成</iBreadcrumbItem>
          </iBreadcrumb>
          <iCard>
            <div>
              <router-view></router-view>
            </div>
          </iCard>
        </iContent>
      </iLayout>
    </iLayout>
  </div>
</template>

<script>
  export default {
    name: "main",
    data() {
      return {
        isCollapsed: false
      };
    },
    computed: {
      menuitemClasses: function () {
        return [
          'menu-item',
          this.isCollapsed ? 'collapsed-menu' : ''
        ]
      }
    }
  }
</script>

<style scoped>
  .layout {
    border: 1px solid #d7dde4;
    background: #f5f7f9;
    position: relative;
    border-radius: 4px;
    overflow: hidden;
  }

  .layout-header-bar {
    background: #fff;
    box-shadow: 0 1px 1px rgba(0, 0, 0, .1);
    display: none;
  }

  .menu-item span {
    display: inline-block;
    overflow: hidden;
    width: 69px;
    text-overflow: ellipsis;
    white-space: nowrap;
    vertical-align: bottom;
    transition: width .2s ease .2s;
  }

  .menu-item i {
    transform: translateX(0px);
    transition: font-size .2s ease, transform .2s ease;
    vertical-align: middle;
    font-size: 16px;
  }

  .collapsed-menu span {
    width: 0px;
    transition: width .2s ease;
  }

  .collapsed-menu i {
    transform: translateX(5px);
    transition: font-size .2s ease .2s, transform .2s ease .2s;
    vertical-align: middle;
    font-size: 22px;
  }
</style>
