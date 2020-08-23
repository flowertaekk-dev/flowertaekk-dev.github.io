---
title: "Firebase with React"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - Firebase
  - React 
toc: true
---

## Firebase with React

### 파이어베이스 세팅

1. [FireBase 콘솔에 접속](https://console.firebase.google.com/)
2. [프로젝트 만들기] 클릭
3. 프로젝트 이름 설정
    * 자유롭게!
4. [계속] 버튼 클릭
5. [Firebase 프로젝트를 위한 Google 애널리틱스] 화면에서 [이 프로젝트에서 Google 애널리틱스 사용 설정]을 OFF로 설정
6. [프로젝트 만들기] 클릭
7. [새 프로젝트가 준비되었습니다.] 화면에서 [계속] 클릭
8. </> 아이콘 클릭
9. [웹 앱에 Firebase 추가] 앱 닉네임 등록
    * 자유롭게!
    * Firebase 호스팅 설정은 하지 말 것!
10. `$npm install firebase`
11. 다음과 같이 코드 설정 (src/firebase.js)
      ```
      import firebase from 'firebase'

      const firebaseConfig = {
          apiKey: "",
          authDomain: "",
          databaseURL: "",
          projectId: "",
          storageBucket: "",
          messagingSenderId: "",
          appId: "
      }

      let database;
      export const fire = () => {
          if (!firebase.apps.length) {
              firebase.initializeApp(firebaseConfig)
          }
          database = firebase.database()
      }

      export const fireDB = () => {
          return database.ref('/').once('value')
      }
      ```
12. App.js
      ```
        import {fire, fireDB} from '../../firebase'
      
        useEffect(() => {
          fire()
        }, [])

        const test = () => {
          fireDB()
            .then(res => {
              console.log(res.val())
            })
        }
      ```
