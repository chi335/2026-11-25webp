# 🚀 Google Apps Script (GAS) 기반 웹 애플리케이션 및 포트폴리오

Google Apps Script(GAS)와 Google Sheets를 연동하여 서버리스(Serverless) 환경에서 작동하는 웹 애플리케이션 모음 및 30년 경력 개발자 스타일의 포트폴리오 프로젝트입니다.

---

## 📋 목차
1. [📌 핵심 개발 개념](#-핵심-개발-개념)
2. [🛠️ GAS 배포 및 구글 시트 연동 방법](#️-gas-배포-및-구글-시트-연동-방법)
3. [📁 프로젝트 1: 개발자 포트폴리오 (OS & 지능형 시스템)](#-프로젝트-1-개발자-포트폴리오-os--지능형-시스템)
4. [📁 프로젝트 2: 11월 25일 저녁 신청 받기 앱](#-프로젝트-2-11월-25일-저녁-신청-받기-앱)
5. [📁 프로젝트 3: 생산성 대시보드 (Kanban Task + Habit Tracker)](#-프로젝트-3-생산성-대시보드-kanban-task--habit-tracker)
6. [🔗 유용한 참고 링크](#-유용한-참고-링크)

---

## 📌 핵심 개발 개념

### 💡 웹 개발 기초 용어
* **프론트엔드 (Frontend)**: 사용자 화면(모니터)에 보이는 웹페이지의 UI/UX를 개발하는 영역.
* **백엔드 (Backend)**: 보안, 데이터베이스(DB) 처리, 서버 통신 등 화면 뒤에서 작동하는 시스템 제어 영역.
* **비즈니스 로직 (Business Logic)**: 사용자 요구사항을 해결하기 위해 데이터를 가공하고 처리하는 핵심 프로그래밍 로직.

### 🌐 호스팅 플랫폼 특징
* **Netlify**: GitHub 저장소와 연동하여 자동 빌드 및 배포를 지원하는 글로벌 호스팅 서비스.
* **닷홈 (Dothome)**: 국내 웹 호스팅 서비스.
* **GAS (Google Apps Script)**: 구글 드라이브와 구글 시트를 백엔드 DB 및 서버로 활용할 수 있는 초간편 호스팅 환경.

---

## 🛠️ GAS 배포 및 구글 시트 연동 방법

```
[Google Sheets (DB)] ◄───► [Code.gs (Backend Logic)] ◄───► [index.html (Frontend UI)]
```

### 1) 구글 시트(DB) 생성 및 설정
1. 구글 드라이브 ➔ **+ 신규** ➔ **Google Sheets (빈 스프레드시트)** 생성.
2. 1행에 헤더 작성 (예: `이름`, `음식`, `하고 싶은 말`).
3. 우측 상단 **[공유]** 클릭 ➔ 일반 액세스: **`링크가 있는 모든 사용자`** / 권한: **`편집자`** 설정 ➔ 완료.
4. **스프레드시트 ID 확인**:
   주소창 `https://docs.google.com/spreadsheets/d/`**`[스프레드시트ID]`**`/edit` 에서 ID 추출.

### 2) Google Apps Script (GAS) 코드 작성
1. 구글 드라이브 ➔ **+ 신규** ➔ **더보기** ➔ **Google Apps Script** 클릭.
2. `Code.gs` 내용 작성 후 저장.
3. 좌측 **[+] (파일 추가)** ➔ **HTML** 선택 ➔ 파일 이름을 `index`로 지정 후 HTML 코드 입력.

### 3) 웹 앱 배포
1. 우측 상단 **[배포]** ➔ **[새 배포]** 클릭.
2. 유형 선택: **웹 앱 (Web App)**.
3. 액세스 권한이 있는 사용자: **`모든 사용자 (Anyone)`** 선택.
4. **[배포]** ➔ **[액세스 승인]** ➔ **[Advanced (고급)]** ➔ **[Go to 프로젝트명 (unsafe)]** ➔ **[Allow (허용)]**.
5. 제공된 **배포 URL** 복사.

### 4) URL 단축 및 QR 코드 생성
* [url.kr](https://url.kr/) 접속 ➔ 배포 URL 입력 ➔ 단축 주소 및 QR 코드 자동 생성.

---

## 📁 프로젝트 1: 개발자 포트폴리오 (OS & 지능형 시스템)

운영체제(OS)의 커널 제어/스케줄링 메커니즘과 지능형 시스템(AI)의 데이터 추론 기술을 강조하는 반응형 포트폴리오 웹사이트입니다.

### 📄 `Code.gs`
```javascript
/**
 * Google Apps Script Web App Entry Point
 * 30년 차 개발자 스타일의 깔끔하고 효율적인 엔트리 포인트
 */

function doGet(e) {
  return HtmlService.createTemplateFromFile('index')
    .evaluate()
    .setTitle('Developer Portfolio | OS & Intelligent Systems')
    .addMetaTag('viewport', 'width=device-width, initial-scale=1.0')
    .setXframeOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

// 이클립스/외부 리소스 포함 시 필요한 헬퍼 함수
function include(filename) {
  return HtmlService.createHtmlOutputFromFile(filename).getContent();
}
```

### 📄 `index.html`
```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>포트폴리오 | 운영체제 & 지능형시스템 전문가</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              dark: '#0B0F19',
              card: '#111827',
              accentOS: '#06B6D4', // Cyan for OS/Kernel
              accentAI: '#8B5CF6', // Purple for Intelligent Systems
            }
          }
        }
      }
    }
  </script>
  <style>
    @import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css');
    body { font-family: 'Pretendard', sans-serif; }
  </style>
</head>
<body class="bg-brand-dark text-slate-100 min-h-screen antialiased selection:bg-brand-accentOS selection:text-black">

  <!-- Main Container -->
  <div class="max-w-5xl mx-auto px-6 py-12">

    <!-- Header Section (Profile & Initials) -->
    <header class="flex flex-col md:flex-row items-center gap-8 p-8 rounded-2xl bg-brand-card border border-slate-800 shadow-2xl relative overflow-hidden">
      <!-- Glow Background Effect -->
      <div class="absolute -top-24 -left-24 w-60 h-60 bg-brand-accentOS/20 rounded-full blur-3xl pointer-events-none"></div>
      <div class="absolute -bottom-24 -right-24 w-60 h-60 bg-brand-accentAI/20 rounded-full blur-3xl pointer-events-none"></div>

      <!-- Initial Avatar (Dynamic SVG Graphic) -->
      <div class="relative shrink-0">
        <div class="w-32 h-32 rounded-full bg-gradient-to-tr from-brand-accentOS via-indigo-500 to-brand-accentAI p-1 shadow-lg shadow-cyan-500/20">
          <div class="w-full h-full bg-slate-950 rounded-full flex items-center justify-center">
            <!-- 사용자의 이니셜 (예: OS & IS / DEV) -->
            <span class="text-3xl font-extrabold tracking-wider bg-clip-text text-transparent bg-gradient-to-r from-cyan-400 to-purple-400">
              DEV
            </span>
          </div>
        </div>
        <span class="absolute bottom-1 right-1 w-5 h-5 bg-emerald-500 border-4 border-slate-950 rounded-full" title="Available for Architecting"></span>
      </div>

      <!-- Info -->
      <div class="text-center md:text-left space-y-3">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full text-xs font-semibold bg-slate-800 border border-slate-700 text-cyan-400">
          <span class="w-2 h-2 rounded-full bg-cyan-400 animate-pulse"></span>
          System Architect & AI Engineer
        </div>
        <h1 class="text-3xl md:text-4xl font-bold tracking-tight text-white">
          시스템의 깊은 곳부터 지능형 알고리즘까지
        </h1>
        <p class="text-slate-400 max-w-xl text-sm leading-relaxed">
          운영체제(OS)의 하드웨어 제어 및 스케줄링 메커니즘과 지능형 시스템(Intelligent Systems)의 데이터 추론 기술을 결합하여 고성능·고효율 소프트웨어를 설계합니다.
        </p>
      </div>
    </header>

    <!-- Core Specialties (주요 전공 및 강조 영역) -->
    <section class="mt-12">
      <h2 class="text-xl font-bold text-white mb-6 flex items-center gap-2">
        <span class="text-brand-accentOS">⚡</span> Core Specialties (전공 핵심 역량)
      </h2>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- 1. Operating Systems -->
        <div class="p-6 rounded-xl bg-brand-card border border-slate-800 hover:border-cyan-500/50 transition-all duration-300 group">
          <div class="w-12 h-12 rounded-lg bg-cyan-950/80 border border-cyan-500/30 flex items-center justify-center text-cyan-400 mb-4 group-hover:scale-110 transition-transform">
            🖥️
          </div>
          <h3 class="text-lg font-bold text-white mb-2 group-hover:text-cyan-400 transition-colors">
            운영체제 (Operating Systems)
          </h3>
          <p class="text-slate-400 text-sm leading-relaxed mb-4">
            시스템 리소스 관리, 커널 구조 이해, 멀티스레딩 동기화 및 메모리 최적화를 통해 시스템의 한계를 극대화하는 로우레벨 아키텍처를 설계합니다.
          </p>
          <div class="flex flex-wrap gap-2 text-xs font-mono">
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Kernel Architecture</span>
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Concurrency & IPC</span>
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Memory Management</span>
          </div>
        </div>

        <!-- 2. Intelligent Systems -->
        <div class="p-6 rounded-xl bg-brand-card border border-slate-800 hover:border-purple-500/50 transition-all duration-300 group">
          <div class="w-12 h-12 rounded-lg bg-purple-950/80 border border-purple-500/30 flex items-center justify-center text-purple-400 mb-4 group-hover:scale-110 transition-transform">
            🧠
          </div>
          <h3 class="text-lg font-bold text-white mb-2 group-hover:text-purple-400 transition-colors">
            지능형 시스템 (Intelligent Systems)
          </h3>
          <p class="text-slate-400 text-sm leading-relaxed mb-4">
            데이터 기반 자율 판단 알고리즘, 머신러닝 모델 경량화 및 실시간 에지 추론(Edge Inference) 시스템을 구현합니다.
          </p>
          <div class="flex flex-wrap gap-2 text-xs font-mono">
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Pattern Recognition</span>
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Edge AI</span>
            <span class="px-2.5 py-1 rounded bg-slate-800 text-slate-300">Automated Reasoning</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Hobbies & Personal Interests (취미 영역) -->
    <section class="mt-12">
      <h2 class="text-xl font-bold text-white mb-6 flex items-center gap-2">
        <span class="text-brand-accentAI">🎯</span> Beyond Coding (취미 및 관심사)
      </h2>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- Ball Sports -->
        <div class="p-6 rounded-xl bg-slate-900/50 border border-slate-800/80 flex items-start gap-4">
          <div class="text-3xl p-3 bg-slate-800 rounded-xl shrink-0">
            🏀
          </div>
          <div>
            <h4 class="font-bold text-white mb-1">구기 종목 (Ball Sports)</h4>
            <p class="text-xs text-slate-400 leading-relaxed">
              축구, 농구, 야구 등 규율 안에서 팀워크와 전략적 패스를 통해 승리를 도출해 내는 역동적인 스포츠를 즐깁니다. 코트 위에서의 전략 실행은 프로젝트 협업 과정과 닮아있습니다.
            </p>
          </div>
        </div>

        <!-- Pokémon -->
        <div class="p-6 rounded-xl bg-slate-900/50 border border-slate-800/80 flex items-start gap-4">
          <div class="text-3xl p-3 bg-slate-800 rounded-xl shrink-0">
            ⚡
          </div>
          <div>
            <h4 class="font-bold text-white mb-1">포켓몬 (Pokémon)</h4>
            <p class="text-xs text-slate-400 leading-relaxed">
              상성 분석, 개체값/수치 계산, 수집 및 배틀 메커니즘을 탐구하는 포켓몬의 깊이 있는 세계관을 좋아합니다. 데이터 수집과 최적화 조합 분석의 또 다른 즐거움입니다.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="mt-16 pt-8 border-t border-slate-800 text-center text-xs text-slate-500">
      <p>© 2026 Developer Portfolio. Built on Google Apps Script Engine.</p>
    </footer>

  </div>

</body>
</html>
```

---

## 📁 프로젝트 2: 11월 25일 저녁 신청 받기 앱

사용자 입력을 구글 스프레드시트에 실시간으로 기록하는 양식 제출용 웹앱입니다.

### 📄 `Code.gs`
```javascript
/**
 * 웹 앱 진입점
 */
function doGet(e) {
  return HtmlService.createTemplateFromFile('index')
    .evaluate()
    .setTitle('11월25일 저녁 신청 받기')
    .addMetaTag('viewport', 'width=device-width, initial-scale=1.0')
    .setXframeOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

/**
 * 폼 제출 처리 및 구글 시트 저장
 */
function submitForm(data) {
  try {
    const ss = SpreadsheetApp.getActiveSpreadsheet();
    let sheet = ss.getActiveSheet();

    // 시트가 비어있을 경우 헤더 자동 추가
    if (sheet.getLastRow() === 0) {
      sheet.appendRow(['이름', '음식', '하고 싶은 말']);
      sheet.getRange(1, 1, 1, 3).setFontWeight('bold').setBackground('#F3F4F6');
    }

    // 데이터 저장 (이름, 음식, 하고 싶은 말)
    sheet.appendRow([
      data.name,
      data.food,
      data.comment
    ]);

    return { success: true };
  } catch (error) {
    return { success: false, message: error.toString() };
  }
}
```

### 📄 `index.html`
```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>11월25일 저녁 신청 받기</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css');
    body { font-family: 'Pretendard', sans-serif; }
  </style>
</head>
<body class="bg-slate-100 min-h-screen flex items-center justify-center p-4">

  <div class="max-w-md w-full bg-white rounded-2xl shadow-xl p-8 border border-slate-200">
    
    <!-- 타이틀 -->
    <div class="text-center mb-6">
      <h1 class="text-2xl font-bold text-slate-800">11월25일 저녁 신청 받기</h1>
      <p class="text-sm text-slate-500 mt-1">저녁 메뉴와 전달사항을 적어주세요.</p>
    </div>

    <!-- 입력 폼 -->
    <form id="menuForm" class="space-y-5" onsubmit="handleSubmit(event)">
      <!-- 이름 -->
      <div>
        <label for="name" class="block text-sm font-semibold text-slate-700 mb-1">이름 <span class="text-red-500">*</span></label>
        <input type="text" id="name" required placeholder="이름을 입력하세요"
          class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm">
      </div>

      <!-- 음식 -->
      <div>
        <label for="food" class="block text-sm font-semibold text-slate-700 mb-1">음식 <span class="text-red-500">*</span></label>
        <input type="text" id="food" required placeholder="드시고 싶은 음식을 입력하세요"
          class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm">
      </div>

      <!-- 하고 싶은 말 -->
      <div>
        <label for="comment" class="block text-sm font-semibold text-slate-700 mb-1">하고 싶은 말</label>
        <textarea id="comment" rows="3" placeholder="남기실 말씀이 있다면 작성해 주세요"
          class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm resize-none"></textarea>
      </div>

      <!-- 제출 버튼 -->
      <button type="submit" id="submitBtn"
        class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3.5 rounded-lg shadow-md transition duration-200 flex items-center justify-center">
        <span>확인</span>
      </button>
    </form>

    <!-- 완료 메시지 영역 (기본적으로 숨김 처리) -->
    <div id="successMessage" class="hidden text-center py-8 space-y-3">
      <div class="w-16 h-16 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center mx-auto text-3xl">
        ✓
      </div>
      <h2 class="text-2xl font-bold text-slate-800">답장 감사합니다.</h2>
      <p class="text-sm text-slate-500">신청이 성공적으로 완료되었습니다.</p>
    </div>

  </div>

  <script>
    function handleSubmit(event) {
      event.preventDefault();

      const submitBtn = document.getElementById('submitBtn');
      submitBtn.disabled = true;
      submitBtn.innerHTML = '<span class="animate-pulse">저장 중...</span>';

      const formData = {
        name: document.getElementById('name').value,
        food: document.getElementById('food').value,
        comment: document.getElementById('comment').value
      };

      // 구글 앱스 스크립트 서버 함수 호출
      google.script.run
        .withSuccessHandler(onSuccess)
        .withFailureHandler(onFailure)
        .submitForm(formData);
    }

    function onSuccess(response) {
      if (response.success) {
        document.getElementById('menuForm').classList.add('hidden');
        document.getElementById('successMessage').classList.remove('hidden');
      } else {
        alert('저장 중 오류가 발생했습니다: ' + response.message);
        resetBtn();
      }
    }

    function onFailure(error) {
      alert('서버통신 오류: ' + error);
      resetBtn();
    }

    function resetBtn() {
      const submitBtn = document.getElementById('submitBtn');
      submitBtn.disabled = false;
      submitBtn.innerText = '확인';
    }
  </script>
</body>
</html>
```

---

## 📁 프로젝트 3: 생산성 대시보드 (Kanban Task + Habit Tracker)

칸반 형태의 할 일 관리 및 일간 습관 달성도(Streak)를 데이터베이스에 동기화하는 대시보드입니다.

### 📄 `Code.gs`
```javascript
/**
 * 구글 앱스 스크립트 웹앱 진입점
 */
function doGet(e) {
  return HtmlService.createTemplateFromFile('index')
    .evaluate()
    .setTitle('My Productivity Hub | 스마트 대시보드')
    .addMetaTag('viewport', 'width=device-width, initial-scale=1.0')
    .setXframeOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

/**
 * 시트 데이터 초기화 및 가져오기
 */
function getDashboardData() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  
  // 1. Tasks 시트 점검 및 생성
  let taskSheet = ss.getSheetByName('Tasks');
  if (!taskSheet) {
    taskSheet = ss.insertSheet('Tasks');
    taskSheet.appendRow(['ID', 'Title', 'Priority', 'Status', 'CreatedAt']);
    taskSheet.getRange(1, 1, 1, 5).setFontWeight('bold').setBackground('#E5E7EB');
  }

  // 2. Habits 시트 점검 및 생성
  let habitSheet = ss.getSheetByName('Habits');
  if (!habitSheet) {
    habitSheet = ss.insertSheet('Habits');
    habitSheet.appendRow(['ID', 'Name', 'Streak', 'LastDoneDate']);
    habitSheet.getRange(1, 1, 1, 4).setFontWeight('bold').setBackground('#E5E7EB');
  }

  // 데이터 읽기
  const tasksRaw = taskSheet.getDataRange().getValues();
  const habitsRaw = habitSheet.getDataRange().getValues();

  const tasks = tasksRaw.slice(1).map(row => ({
    id: row[0],
    title: row[1],
    priority: row[2],
    status: row[3],
    createdAt: row[4]
  }));

  const habits = habitsRaw.slice(1).map(row => ({
    id: row[0],
    name: row[1],
    streak: row[2] || 0,
    lastDoneDate: row[3] || ''
  }));

  return { tasks, habits };
}

/**
 * 새 할 일 추가
 */
function addTask(title, priority) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName('Tasks');
  const id = 'task_' + Date.now();
  const createdAt = new Date().toLocaleDateString('ko-KR');
  
  sheet.appendRow([id, title, priority, 'TODO', createdAt]);
  return { id, title, priority, status: 'TODO', createdAt };
}

/**
 * 할 일 상태 변경 (TODO -> IN_PROGRESS -> DONE)
 */
function updateTaskStatus(id, newStatus) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName('Tasks');
  const data = sheet.getDataRange().getValues();

  for (let i = 1; i < data.length; i++) {
    if (data[i][0] === id) {
      sheet.getRange(i + 1, 4).setValue(newStatus);
      return { success: true };
    }
  }
  return { success: false };
}

/**
 * 할 일 삭제
 */
function deleteTask(id) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName('Tasks');
  const data = sheet.getDataRange().getValues();

  for (let i = 1; i < data.length; i++) {
    if (data[i][0] === id) {
      sheet.deleteRow(i + 1);
      return { success: true };
    }
  }
  return { success: false };
}

/**
 * 습관 추가
 */
function addHabit(name) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName('Habits');
  const id = 'habit_' + Date.now();
  
  sheet.appendRow([id, name, 0, '']);
  return { id, name, streak: 0, lastDoneDate: '' };
}

/**
 * 오늘 습관 체크 / 해제
 */
function toggleHabit(id) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName('Habits');
  const data = sheet.getDataRange().getValues();
  const todayStr = new Date().toISOString().split('T')[0];

  for (let i = 1; i < data.length; i++) {
    if (data[i][0] === id) {
      let streak = parseInt(data[i][2]) || 0;
      let lastDone = data[i][3];

      if (lastDone === todayStr) {
        // 오늘 이미 완료했던 경우 -> 취소
        streak = Math.max(0, streak - 1);
        lastDone = '';
      } else {
        // 오늘 첫 완료
        streak += 1;
        lastDone = todayStr;
      }

      sheet.getRange(i + 1, 3).setValue(streak);
      sheet.getRange(i + 1, 4).setValue(lastDone);
      return { success: true, streak, lastDone };
    }
  }
  return { success: false };
}
```

### 📄 `index.html`
```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Productivity & Lifestyle Hub</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css');
    body { font-family: 'Pretendard', sans-serif; }
  </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen p-4 md:p-8 selection:bg-indigo-500 selection:text-white">

  <div class="max-w-7xl mx-auto space-y-8">

    <!-- Header Section -->
    <header class="flex flex-col md:flex-row justify-between items-start md:items-center p-6 bg-slate-900 border border-slate-800 rounded-2xl shadow-xl gap-4">
      <div>
        <div class="flex items-center gap-3">
          <h1 class="text-2xl font-bold text-white tracking-tight">⚡ Personal Productivity Hub</h1>
          <span class="px-3 py-1 bg-indigo-500/10 text-indigo-400 text-xs font-semibold rounded-full border border-indigo-500/20">v1.0</span>
        </div>
        <p class="text-xs text-slate-400 mt-1">칸반 투두 관리와 데일리 습관 트래커로 하루의 효율성을 극대화하세요.</p>
      </div>
      <div class="text-right">
        <div id="currentDateText" class="text-sm font-semibold text-indigo-400">2026년 11월 25일 수요일</div>
        <div class="text-xs text-slate-500 mt-0.5">Google Sheets DB Synced</div>
      </div>
    </header>

    <!-- Main Grid Layout (Kanban + Habits) -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">

      <!-- Left 2 Columns: Kanban Board (Tasks) -->
      <div class="lg:col-span-2 space-y-6">
        
        <!-- Task Header & Add Form -->
        <div class="p-6 bg-slate-900 border border-slate-800 rounded-2xl shadow-md">
          <h2 class="text-lg font-bold text-white mb-4 flex items-center gap-2">
            <span>📋</span> 할 일 등록 (Task Manager)
          </h2>
          <form onsubmit="handleAddTask(event)" class="flex flex-col sm:flex-row gap-3">
            <input type="text" id="taskTitle" required placeholder="새로운 할 일을 입력하세요..."
              class="flex-1 px-4 py-2.5 rounded-xl bg-slate-950 border border-slate-800 text-sm focus:outline-none focus:border-indigo-500 text-slate-200">
            <select id="taskPriority" class="px-4 py-2.5 rounded-xl bg-slate-950 border border-slate-800 text-sm focus:outline-none focus:border-indigo-500 text-slate-300">
              <option value="보통">보통 우선순위</option>
              <option value="높음">🔥 높음</option>
              <option value="낮음">☕ 낮음</option>
            </select>
            <button type="submit" class="px-5 py-2.5 bg-indigo-600 hover:bg-indigo-500 text-white font-semibold text-sm rounded-xl transition shadow-lg shadow-indigo-600/30">
              추가
            </button>
          </form>
        </div>

        <!-- Kanban Columns -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
          <!-- TODO Column -->
          <div class="p-4 bg-slate-900/60 border border-slate-800 rounded-2xl">
            <div class="flex items-center justify-between mb-4">
              <h3 class="text-sm font-bold text-slate-400 flex items-center gap-2">
                <span class="w-2.5 h-2.5 rounded-full bg-amber-400"></span> 대기 (TODO)
              </h3>
              <span id="count-TODO" class="text-xs bg-slate-800 px-2 py-0.5 rounded text-slate-400">0</span>
            </div>
            <div id="col-TODO" class="space-y-3 min-h-[300px]"></div>
          </div>

          <!-- IN_PROGRESS Column -->
          <div class="p-4 bg-slate-900/60 border border-slate-800 rounded-2xl">
            <div class="flex items-center justify-between mb-4">
              <h3 class="text-sm font-bold text-slate-400 flex items-center gap-2">
                <span class="w-2.5 h-2.5 rounded-full bg-indigo-400"></span> 진행 중 (IN PROGRESS)
              </h3>
              <span id="count-IN_PROGRESS" class="text-xs bg-slate-800 px-2 py-0.5 rounded text-slate-400">0</span>
            </div>
            <div id="col-IN_PROGRESS" class="space-y-3 min-h-[300px]"></div>
          </div>

          <!-- DONE Column -->
          <div class="p-4 bg-slate-900/60 border border-slate-800 rounded-2xl">
            <div class="flex items-center justify-between mb-4">
              <h3 class="text-sm font-bold text-slate-400 flex items-center gap-2">
                <span class="w-2.5 h-2.5 rounded-full bg-emerald-400"></span> 완료 (DONE)
              </h3>
              <span id="count-DONE" class="text-xs bg-slate-800 px-2 py-0.5 rounded text-slate-400">0</span>
            </div>
            <div id="col-DONE" class="space-y-3 min-h-[300px]"></div>
          </div>
        </div>

      </div>

      <!-- Right 1 Column: Daily Habit Tracker -->
      <div class="space-y-6">
        
        <div class="p-6 bg-slate-900 border border-slate-800 rounded-2xl shadow-md">
          <h2 class="text-lg font-bold text-white mb-4 flex items-center gap-2">
            <span>🔥</span> 데일리 습관 트래커
          </h2>
          
          <form onsubmit="handleAddHabit(event)" class="flex gap-2 mb-6">
            <input type="text" id="habitName" required placeholder="새 습관 (예: 독서 30분)..."
              class="flex-1 px-4 py-2 rounded-xl bg-slate-950 border border-slate-800 text-sm focus:outline-none focus:border-indigo-500 text-slate-200">
            <button type="submit" class="px-4 py-2 bg-emerald-600 hover:bg-emerald-500 text-white text-sm font-semibold rounded-xl transition">
              등록
            </button>
          </form>

          <div id="habitList" class="space-y-3">
            <!-- Habits rendered here -->
          </div>
        </div>

        <!-- Quick Summary Box -->
        <div class="p-6 bg-gradient-to-br from-indigo-900/40 to-purple-900/40 border border-indigo-500/20 rounded-2xl">
          <h3 class="text-sm font-bold text-indigo-300 mb-2">💡 오늘의 생산성 팁</h3>
          <p class="text-xs text-slate-300 leading-relaxed">
            중요도가 높은 일은 '진행 중'에 최대 2개까지만 올려두고 집중하세요. 습관은 연속 달성(Streak)이 길어질수록 강력한 패턴이 됩니다!
          </p>
        </div>

      </div>

    </div>

  </div>

  <script>
    let state = { tasks: [], habits: [] };
    const todayStr = new Date().toISOString().split('T')[0];

    window.onload = function() {
      // 날짜 세팅
      const now = new Date();
      document.getElementById('currentDateText').innerText = `${now.getFullYear()}년 ${now.getMonth()+1}월 ${now.getDate()}일`;
      
      fetchData();
    };

    function fetchData() {
      google.script.run.withSuccessHandler(data => {
        state.tasks = data.tasks;
        state.habits = data.habits;
        render();
      }).getDashboardData();
    }

    // ---------------- TASK HANDLERS ----------------
    function handleAddTask(e) {
      e.preventDefault();
      const title = document.getElementById('taskTitle').value;
      const priority = document.getElementById('taskPriority').value;

      google.script.run.withSuccessHandler(newTask => {
        state.tasks.push(newTask);
        document.getElementById('taskTitle').value = '';
        render();
      }).addTask(title, priority);
    }

    function moveTask(id, nextStatus) {
      const task = state.tasks.find(t => t.id === id);
      if (task) {
        task.status = nextStatus;
        render();
        google.script.run.updateTaskStatus(id, nextStatus);
      }
    }

    function removeTask(id) {
      state.tasks = state.tasks.filter(t => t.id !== id);
      render();
      google.script.run.deleteTask(id);
    }

    // ---------------- HABIT HANDLERS ----------------
    function handleAddHabit(e) {
      e.preventDefault();
      const name = document.getElementById('habitName').value;

      google.script.run.withSuccessHandler(newHabit => {
        state.habits.push(newHabit);
        document.getElementById('habitName').value = '';
        render();
      }).addHabit(name);
    }

    function toggleHabit(id) {
      const habit = state.habits.find(h => h.id === id);
      if (habit) {
        const isDone = habit.lastDoneDate === todayStr;
        habit.lastDoneDate = isDone ? '' : todayStr;
        habit.streak = isDone ? Math.max(0, habit.streak - 1) : habit.streak + 1;
        render();
        google.script.run.toggleHabit(id);
      }
    }

    // ---------------- RENDER UI ----------------
    function render() {
      // 1. Render Tasks
      ['TODO', 'IN_PROGRESS', 'DONE'].forEach(status => {
        const container = document.getElementById(`col-${status}`);
        const filtered = state.tasks.filter(t => t.status === status);
        document.getElementById(`count-${status}`).innerText = filtered.length;

        container.innerHTML = filtered.map(task => `
          <div class="p-3.5 bg-slate-950 border border-slate-800 rounded-xl space-y-2 group hover:border-slate-700 transition">
            <div class="flex items-start justify-between gap-2">
              <span class="text-xs text-slate-200 font-medium leading-snug">${task.title}</span>
              <button onclick="removeTask('${task.id}')" class="text-xs text-slate-600 hover:text-red-400 opacity-0 group-hover:opacity-100 transition">✕</button>
            </div>
            <div class="flex items-center justify-between pt-1 text-[11px]">
              <span class="px-2 py-0.5 rounded ${getPriorityBadge(task.priority)} font-mono">${task.priority}</span>
              <div class="flex gap-1">
                ${status !== 'TODO' ? `<button onclick="moveTask('${task.id}', '${getPrevStatus(status)}')" class="px-1.5 py-0.5 bg-slate-800 text-slate-400 rounded hover:bg-slate-700">◀</button>` : ''}
                ${status !== 'DONE' ? `<button onclick="moveTask('${task.id}', '${getNextStatus(status)}')" class="px-1.5 py-0.5 bg-slate-800 text-slate-400 rounded hover:bg-slate-700">▶</button>` : ''}
              </div>
            </div>
          </div>
        `).join('');
      });

      // 2. Render Habits
      const habitList = document.getElementById('habitList');
      habitList.innerHTML = state.habits.map(habit => {
        const isChecked = habit.lastDoneDate === todayStr;
        return `
          <div class="flex items-center justify-between p-3 bg-slate-950 border border-slate-800 rounded-xl">
            <div class="flex items-center gap-3">
              <button onclick="toggleHabit('${habit.id}')" 
                class="w-6 h-6 rounded-lg border ${isChecked ? 'bg-emerald-500 border-emerald-500 text-black' : 'border-slate-700 bg-slate-900'} flex items-center justify-center font-bold text-xs transition">
                ${isChecked ? '✓' : ''}
              </button>
              <span class="text-sm font-medium ${isChecked ? 'line-through text-slate-500' : 'text-slate-200'}">${habit.name}</span>
            </div>
            <div class="flex items-center gap-1 px-2.5 py-1 bg-amber-500/10 border border-amber-500/20 rounded-full text-xs font-semibold text-amber-400">
              🔥 ${habit.streak}일 연속
            </div>
          </div>
        `;
      }).join('');
    }

    function getPriorityBadge(priority) {
      if (priority === '높음') return 'bg-red-500/10 text-red-400 border border-red-500/20';
      if (priority === '낮음') return 'bg-slate-800 text-slate-400';
      return 'bg-indigo-500/10 text-indigo-400 border border-indigo-500/20';
    }

    function getNextStatus(s) { return s === 'TODO' ? 'IN_PROGRESS' : 'DONE'; }
    function getPrevStatus(s) { return s === 'DONE' ? 'IN_PROGRESS' : 'TODO'; }
  </script>
</body>
</html>
```

---

## 🔗 유용한 참고 링크
* 🗺️ [Developer Roadmap (Roadmap.sh)](https://roadmap.sh/) - 직무별 학습 로드맵
* 🔗 [URL 단축기 & QR 코드 생성기](https://url.kr/)
* 🌐 [Netlify 공식 페이지](https://www.netlify.com/)
