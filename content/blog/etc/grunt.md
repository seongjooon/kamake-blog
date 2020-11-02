---
title: 'Grunt'
date: 2020-10-19 17:10:08
category: 'etc'
---

> ## Gruntfile의 구성

- The "wrapper" function
- Project and task configuration
- Loading Grunt plugins and tasks
- Custom tasks

실수나 반복적인 작업을 줄이기 위한 자동화 툴입니다.
Grunt vs Gulp
위처럼 둘은 같은 작업을 수행하지만, 수행하는 방법에서 차이가 있습니다.
설정 파일 기반의 Grunt와 달리 Gulp는 JavaScript 코드를 다룰줄 아는 사람이면 쉽게 다룰 수 있습니다.

grunt는 릴리즈가 느립니다.

결론부터 말하자면 Webpack이 이들을 대체된다기 보다 이 기능이 포함되어 있고 더 많은 작업을 할 수 있기 때문에 이 도구를 사용하는 것입니다. Webpack은 Browserify와 같은 의존성 관리 기능까지 포함하고 있으니 “webpack = (Grunt||Gulp) + Browserify” 이게 되는 것입니다. 게다가 속도도 빠른 편입니다.

> 기본 형식

```js
module.exports = function (grunt) {
  // 1. 프로젝트의 구성
  // grunt.initConfig() 메서드에 전달된 객체에 정의된 데이터에 의존합니다.
  grunt.initConfig({
    // package.json의 정보를 불러옴
    pkg: grunt.file.readJSON('package.json'),

    // uglify 플러그인(패키지)의 옵션을 정의 함
    uglify: {
      build: {
        src: 'src/<%= pkg.name %>.js',
        dest: 'build/<%= pkg.name %>.min.js',
      },
    },
  })

  // 2. 사용한 플러그인 로딩(먼저 npm으로 설치를 해야 함)
  grunt.loadNpmTasks('grunt-contrib-uglify')

  // 3. 실행 명령어 (명령창에서 grunt 명령으로 실행됨)
  grunt.registerTask('default', ['uglify'])
}
```

> grunt-contrib-uglify

JS파일을 압축합니다. 빈 공간과 줄바꿈, 주석 등 불필요한 모든 요소를 제거합니다. 압축한 파일을 dist에 저장합니다.

> grunt-contrib-watch

개발 시 지정한 폴더의 파일의 변경 유무를 실시간으로 보고 있다가 변경이 감지되면 지정한 명령어를 실행해 주는 플러그인입니다.

```js
watch: {
  scripts: {
    files: ['**/*.js'],
    tasks: ['jshint','uglify'] // 변경이 일어나면 tasks에 지정된 명령어 jshint,uglify 를 순차적으로 실행함
  }
}
```

> grunt-contrib-concat

2개 이상의 javascript나 css 파일을 하나의 파일로 합쳐주는 플러그인 입니다.
src에 지정되어 있는 파일을 합쳐서 하나의 파일로 만들어서 dest에 지정된 폴더인 dist/에 지정된 파일명인 built.js로 저장합니다.

```js
concat: {
  options: { separator: ';', },
  dist: {
    src: ['src/intro.js', 'src/project.js', 'src/outro.js'],
    dest: 'dist/built.js'
  }
}
```

> sprite

이미지를 하나의 파일로 만들어주는 역할을 합니다.
