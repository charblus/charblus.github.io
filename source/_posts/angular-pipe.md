---
title: ngular6开发不完全笔记（一）-- 管道
categories:
  - 前端
  - angular
tags:
  - 前端
  - angular
comments: false
abbrlink: 1184
date: 2019-01-10 03:43:12
img:
---

> 自定义管道 管道（过滤器）为过滤数据显示下列list数据

* pip.ts 文件
 ```ts
import { Pipe, PipeTransform } from '@angular/core';
import { TableType } from './add-student.service';

@Pipe({
  name: 'studyProjectType'
})
export class StudyProjectTypePipe implements PipeTransform {
  transform( allstudyProjects: any[], typeParams: any): any {
    // console.log(typeParams);
    return allstudyProjects.filter(type => typeParams.indexOf(type.type) !== -1);
  }
}
 ```

transform 方法是管道的基本要素。 PipeTransform接口中定义了它. 当每个输入值被传给 transform 方法时，还会带上另一个参数
allstudyProjects 是输入值 ，也就是html 页面中 `|`  前面的studyProjectList是管道名   typeParams是管道名后的参数 传进管道中
以上这两个为形参，名字自定义，建议命名规范，尤其是写分享管道 . transform 函数里return 是输入数据过滤filter，里面是一个函数

> 这里的思路是 对比 请求下的数据 studyProjectList 每个列表的type属性 对比下面typeParams, 结果为true 就通过过滤显示

本地数据来源
```
public types: TabType[] = [
    {
      name: '课程',
      id: 'courseDate',
      tags: ['在线课', '线上课', '直播课', '线下课'],
    },
    {
      name: '考试',
      id: 'examDate',
      tags: ['试卷'],
    },
    {
      name: '作业',
      id: 'taskDate',
      tags: ['作业'],
    },
    {
      name: '问卷',
      id: 'questionnaireDate',
      tags: ['问卷'],
    },
  ];
  private typeParams: string[] = this.types[0].tags;    //初始值
```

* html 文件
```
  <div class="table-responsive">
    <!-- {{ studyProjectList | studyProjectType }} -->
    <app-project-assign-list  [studyProjectList] = "studyProjectList | studyProjectType: typeParams "></app-project-assign-list>
  </div>
```
> app-project-assign-list 为列表样式组件
```
  //click 点击事件 改变types[i]
  switchType (i) {
    this.typeParams = this.types[i].tags;
  }
```

线上数据来源
```
 /*
 * 数据来源 
 * addStudentService 服务提供 getStudyProject方法
  */
 dataSource: Observable<any>;
  // studyProjectList: Array<any> = [];
   studyProjectList: TableType[] = [];
  constructor(
    private addStudentService: AddStudentService,
  ) {
  }

  ngOnInit() {
    this.dataSource = this.addStudentService.getStudyProject();
    this.dataSource.subscribe(
      (data) => {
        console.log(data);
        this.studyProjectList = data.students;
      }
    );
  }
```