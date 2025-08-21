<template>
  <div class="document-container">
    <el-card class="document-card">
      <template #header>
        <div class="card-header">
          <h1>项目简介</h1>
        </div>
      </template>

      <div class="document-content">
        <p class="description" style="text-align: center">
          提供标准化的 Spring 分层架构代码 + MyBatis 的 CRUD 代码生成。基于 FreeMarker
          模板引擎实现。
        </p>

        <el-divider content-position="center">
          <el-icon><Star /></el-icon>
          <span class="divider-text">感谢使用</span>
        </el-divider>
      </div>
    </el-card>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import {
  InfoFilled,
  Setting,
  Guide,
  Document,
  QuestionFilled,
  Star,
  Link
} from '@element-plus/icons-vue'

// 折叠面板的激活项
const activeNames = ref(['1'])

// 参数说明数据
const parameterData = ref([
  {
    parameter: 'projectName',
    type: 'String',
    required: true,
    description: '项目名称，用于生成项目相关的配置和文件名'
  },
  {
    parameter: 'author',
    type: 'String',
    required: true,
    description: '作者名称，会在生成的代码注释中显示'
  },
  {
    parameter: 'packageName',
    type: 'String',
    required: true,
    description: 'Java项目的包名，例如：com.example.demo'
  },
  {
    parameter: 'dbType',
    type: 'String',
    required: true,
    description: '数据库类型，支持mysql、postgresql、oracle等'
  },
  {
    parameter: 'dbHost',
    type: 'String',
    required: false,
    description: '数据库主机地址，默认为localhost'
  },
  {
    parameter: 'dbPort',
    type: 'Number',
    required: false,
    description: '数据库端口号，默认根据数据库类型自动设置'
  },
  {
    parameter: 'dbName',
    type: 'String',
    required: true,
    description: '数据库名称'
  },
  {
    parameter: 'tables',
    type: 'Array',
    required: true,
    description: '需要生成代码的数据表列表'
  },
  {
    parameter: 'templateType',
    type: 'String',
    required: false,
    description: '代码模板类型，如SpringBoot、MyBatis等'
  },
  {
    parameter: 'outputPath',
    type: 'String',
    required: false,
    description: '代码输出路径，默认为当前目录'
  }
])

// 根据类型返回对应的颜色
const getTypeColor = (type) => {
  const colorMap = {
    String: 'success',
    Number: 'warning',
    Array: 'info',
    Boolean: 'danger'
  }
  return colorMap[type] || 'primary'
}

// 打开GitHub仓库
const openGithub = () => {
  window.open('https://github.com/lingyjava/auto-coder', '_blank')
}
</script>

<style lang="scss" scoped>
.document-container {
  padding: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

.document-card {
  .card-header {
    text-align: center;

    h1 {
      margin: 0;
      color: #409eff;
      font-weight: 600;
    }
  }
}

.document-content {
  .divider-text {
    margin-left: 8px;
    font-weight: 600;
    color: #606266;
  }

  .description {
    font-size: 16px;
    line-height: 1.6;
    color: #606266;
    margin: 20px 0;
    text-align: justify;
  }

  .example-code {
    background: #f5f7fa;
    padding: 15px;
    border-radius: 4px;
    font-family: 'Courier New', monospace;
    font-size: 14px;
    line-height: 1.5;
    color: #2c3e50;
    margin: 0;
    white-space: pre-wrap;
  }

  .thank-you {
    text-align: center;
    padding: 30px 0;

    p {
      font-size: 16px;
      color: #606266;
      margin-bottom: 20px;
    }
  }

  .el-steps {
    margin: 30px 0;
  }

  .el-table {
    margin: 20px 0;
  }

  .el-collapse {
    margin: 20px 0;
  }

  .el-alert {
    margin: 20px 0;
  }
}
</style>
