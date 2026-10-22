<!-- ============ HEADER ============ -->
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=220&section=header&text=Sema%20Heybatov&fontSize=56&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=QA%20Manual%20Engineer%20%E2%80%A2%20Sonic%20Academy%20Graduate&descAlignY=60&descSize=18" alt="Sema Heybatov — QA Manual Engineer"/>
</p>

<p align="center">
  <a href="https://github.com/SemaEyvazli">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=800&color=36BCF7&center=true&vCenter=true&multiline=false&width=640&lines=%F0%9F%94%8D+Manual+QA+Engineer;%F0%9F%90%9E+Bug+hunter+%E2%80%94+UI%2C+API%2C+Mobile;%F0%9F%93%AE+Postman+%26+Swagger+API+Testing;%F0%9F%93%9D+Test+Plan+%E2%80%A2+Test+Case+%E2%80%A2+Bug+Report;%F0%9F%9A%80+Real+projects%3A+Smplifai+%26+OnlineTest" alt="Typing SVG" />
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Role-QA%20Manual%20Engineer-0A66C2?style=for-the-badge&logo=checkmarx&logoColor=white"/>
  <img src="https://img.shields.io/badge/Training-Sonic%20Academy-6E40C9?style=for-the-badge&logo=academia&logoColor=white"/>
  <img src="https://img.shields.io/badge/Period-Jul%E2%80%93Oct%202026-2EA44F?style=for-the-badge&logo=googlecalendar&logoColor=white"/>
  <img src="https://img.shields.io/badge/Location-Baku%2C%20AZ-E34F26?style=for-the-badge&logo=googlemaps&logoColor=white"/>
</p>

---

## 👩‍💻 Haqqımda

Mən **Sonic Academy**-nin **QA Manual** proqramını (**İyul – Oktyabr 2026**) bitirmiş, real layihələr üzərində təcrübə qazanmış Manual QA mütəxəssisiyəm.
Təlim-təcrübə proqramı çərçivəsində iki canlı məhsulu test etmişəm, təlimdən sonra isə **OnlineTest** layihəsində **Sonic Lab** komandası ilə işləməyə davam edirəm.

| | Layihə | Nədir | Mənim işim |
|:-:|---|---|---|
| 🎓 | **Smplifai** | Tələbə qeydiyyatı və sənəd avtomatlaşdırma platforması (React + Node.js + Supabase) | Test Plan, Test Case, Checklist, Bug Report, Test Summary Report, UI + API (Swagger/Postman) testləri |
| 📝 | **OnlineTest (onlinetest.az)** | Azərbaycan şagirdləri üçün onlayn imtahan hazırlıq platforması (mikroservis arxitekturası) | `taxonomy-service` üzərində API test keysləri (Swagger UI, API Gateway) |
| 🛒 | **Automation Exercise** | Açıq demo e-commerce saytı | Kəşfiyyat (exploratory) testi və bug reportlar |

> 💡 *"Quality is never an accident; it is always the result of intelligent effort."*

---

## 📖 Repo Story — QA səyahətim

Commit tarixçəsinə əsasən xronologiya:

```mermaid
timeline
    title Sema-nın QA yolu (2026)
    İyul : automation-exercise — e-commerce saytında 3 bug
         : Smplifai — ilk funksional test keyslər və ilk 3 bug report
    Sentyabr : simplifaiapplicationtestcase — TC-001 (My Application)
             : Smplifai API — POST 201 Created, DELETE 200 OK, 401 negativ ssenari
    Oktyabr : testonline.az — taxonomy-service API test keysi
            : simplifaiapplicationtestcase — Checklist, Test Summary Report, bütün işlərin bir repoda toplanması
```

<details open>
<summary><b>🟢 Fəsil 1 — İlk addımlar (İyul)</b></summary>

<br>

**📁 [`automation-exercise`](https://github.com/SemaEyvazli/automation-exercise)**
Açıq demo saytda kəşfiyyat testi — sərhəd dəyərləri və validasiya xətaları:

| ID | Xəta | Texnika |
|---|---|---|
| BUG-001 | Səbətə **mənfi sayda** (-1) məhsul əlavə etmək mümkündür | Boundary Value Analysis |
| BUG-002 | "Contact Us" **yanlış formatlı e-poçtu** qəbul edir | Negative / Validation testing |
| BUG-003 | Çoxlu simvolla axtarışda boş səhifə, "nəticə tapılmadı" mesajı yoxdur | Error Guessing |

**📄 Smplifai — ilk funksional test keyslər** ([`testcase.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/testcase.md))
Tələb sənədindəki bölmələrə əsasən cədvəl formatlı test keyslər: `2.1 Authentication & System Access` (Log In, Student Registration, Logout) və `2.4 Application Lifecycle` (Completeness Tracking).

**📄 Smplifai — ilk real xətalar** ([`bugreport.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/bugreport.md))

| ID | Xəta | Modul | Severity |
|---|---|---|:-:|
| BUG-001 | Şifrə sıfırlama e-poçtu istifadəçiyə çatmır | Password Reset | 🔴 High |
| BUG-002 | Profil şəkli logout → login sonrası silinir | Profile | 🟠 Medium |
| BUG-003 | Mobil cihazda düymə və panellər ekrandan çıxır | Mobile UI | 🔴 High |

</details>

<details open>
<summary><b>🔵 Fəsil 2 — API dünyasına keçid (Sentyabr)</b></summary>

<br>

**📄 [`TC_APP_POST_001`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/smplifai-application-testcase.md)**
Bearer Token ilə `POST /api/applications` sorğusu → **`201 Created`**, cavab JSON-da obyektin `DRAFT` statusunda yaradıldığı yoxlanır.

**📄 [`TC_APP_DEL_001`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/application-delete-TC.md)**
End-to-end ssenari: UI-da müraciət yarat → Swagger-də **Authorize** → `DELETE /api/applications/{id}` → **`200 OK`**.
Negativ ssenari: token olmadan sorğu → **`401 Unauthorized`** (`"success": false`).

</details>

<details open>
<summary><b>🟣 Fəsil 3 — Tam QA sənəd paketi (Oktyabr)</b></summary>

<br>

**📁 [`simplifaiapplicationtestcase`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase)** ⭐ *əsas portfolio layihəsi*

| Sənəd | Məzmun |
|---|---|
| 📋 [`Test Plan`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/6490f8c/README.md) | Objective, In/Out of Scope, Test Types, Environment, Entry/Exit Criteria, Risks & Mitigation, Deliverables |
| 🧪 [`test-cases.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/test-cases.md) | 6 test keys: UI (My Application, Sign In) + API (GET 200, DELETE 200, 401 Unauthorized, 404 Not Found) |
| ✅ [`Checklist.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/Checklist.md) | 13 yoxlama, 4 bölmə: Authentication, Application & File Upload, API Testing, UI/UX & Responsiveness |
| 🐞 [`bugreport.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/bugreport.md) | 3 bug — Preconditions, Steps, Actual/Expected, Severity/Priority |
| 📊 [`Test-Summary-Report.md`](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/Test-Summary-Report.md) | Metrikalar, bug paylanması, yekun QA statusu |

<sub>📊 Rəqəmlər <code>Test-Summary-Report.md</code>-dən götürülüb:</sub>

```text
┌────────────── Test Execution Summary ──────────────┐
│  Total Test Cases ........ 4                       │
│  ✅ Passed ................ 3                       │
│  ❌ Failed ................ 1                       │
│  ⛔ Blocked ............... 0                       │
│  🐞 Bugs Found ............ 3  (High: 2, Medium: 1) │
│  Final Status ............ Conditional Approval    │
└────────────────────────────────────────────────────┘
```

**📁 [`testonline.az`](https://github.com/SemaEyvazli/testonline.az)**
OnlineTest platformasının mikroservis arxitekturasında **API Gateway → Swagger UI → `taxonomy-service`** seçimi ilə `POST /api/v1/exam-definitions` endpoint-i üzərindən yeni imtahan növünün ("Buraxılış imtahanı", 85 sual, 180 dəq, 300 bal) yaradılması test edildi → **Passed** ✅

</details>

---

## 📊 Rəqəmlərlə

<p align="center">
  <img src="https://img.shields.io/badge/QA%20Repositories-3-181717?style=flat-square&logo=github"/>
  <img src="https://img.shields.io/badge/Commits-30%2B-181717?style=flat-square&logo=git&logoColor=F05032"/>
  <img src="https://img.shields.io/badge/Test%20Cases-12-2EA44F?style=flat-square&logo=testinglibrary&logoColor=white"/>
  <img src="https://img.shields.io/badge/Checklist%20Items-13-0A66C2?style=flat-square&logo=checkmarx&logoColor=white"/>
  <img src="https://img.shields.io/badge/Bugs%20Reported-6-D73A49?style=flat-square&logo=bugatti&logoColor=white"/>
  <img src="https://img.shields.io/badge/API%20Endpoints%20Tested-4-FF6C37?style=flat-square&logo=postman&logoColor=white"/>
  <img src="https://img.shields.io/badge/Products%20Tested-3-6E40C9?style=flat-square&logo=databricks&logoColor=white"/>
</p>

<p align="center">
  <img height="165" src="https://streak-stats.demolab.com/?user=SemaEyvazli&theme=tokyonight&hide_border=true" />
</p>

---

## 🎓 Sonic Academy — QA Manual (İyul – Oktyabr 2026)

<details>
<summary><b>📚 Öyrənilən mövzular (19 modul)</b></summary>

<br>

| # | Modul | Mövzular |
|:-:|---|---|
| 1 | 🧭 **Testing əsasları** | QA vs QC vs Testing, Error / Defect / Bug / Failure, 7 test prinsipi, testin məqsədi və dəyəri |
| 2 | 🔄 **SDLC & STLC** | Waterfall, V-Model, Iterative, Agile; STLC mərhələləri (Requirement Analysis → Test Planning → Test Design → Environment Setup → Execution → Closure) |
| 3 | 🏃 **Agile & Scrum** | Rollar (PO, SM, Dev Team), Sprint, Backlog, User Story, Acceptance Criteria, Definition of Done, Daily/Review/Retro, Kanban |
| 4 | 🏗️ **Test səviyyələri** | Unit, Integration, System, Acceptance (UAT, Alpha/Beta) |
| 5 | 🧪 **Test növləri** | Functional / Non-functional, Smoke, Sanity, Regression, Retesting, Exploratory, Ad-hoc, Usability, Compatibility, Cross-browser, Security əsasları, Performance anlayışı |
| 6 | 📦 **Black / White / Grey Box** | Testing yanaşmaları və fərqləri, Static vs Dynamic testing, Review növləri |
| 7 | 🎯 **Test Design texnikaları** | Equivalence Partitioning, Boundary Value Analysis, Decision Table, State Transition, Use Case testing, Error Guessing, Pairwise |
| 8 | 📝 **Test sənədləşməsi** | Test Plan, Test Strategy, Test Scenario, Test Case, Checklist, Test Data, RTM (Requirement Traceability Matrix), Test Summary Report |
| 9 | 🐞 **Bug Management** | Bug Report strukturu, Severity vs Priority, Bug Life Cycle (New → Assigned → Open → Fixed → Retest → Verified → Closed / Reopened / Rejected / Deferred) |
| 10 | 🌐 **Web testing** | Client-Server, HTTP/HTTPS, URL quruluşu, Cookies / Session / Cache, Local & Session Storage, Responsive testing |
| 11 | 🛠️ **Chrome DevTools** | Elements, Console, Network (request/response, status kodlar), Application tab, device emulation |
| 12 | 🔌 **API Testing** | REST, HTTP metodları (GET, POST, PUT, PATCH, DELETE), Status kodlar (2xx/4xx/5xx), Headers, JSON, Query/Path params, Bearer Token autentifikasiya, pozitiv/negativ API ssenariləri |
| 13 | 📮 **Postman & Swagger** | Collection, Environment, Variables, Authorization, Swagger UI ilə endpoint test, API sənədləşməsini oxumaq |
| 14 | 🧩 **Mikroservis anlayışı** | API Gateway, servislərin ayrılması, staging mühit |
| 15 | 📱 **Mobile testing** | Android/iOS fərqləri, real cihaz vs emulator, responsive UI yoxlamaları |
| 16 | 🗄️ **SQL əsasları** | SELECT, WHERE, JOIN, ORDER BY, GROUP BY — backend data yoxlaması |
| 17 | 📋 **Jira** | Project, Issue types (Epic, Story, Task, Bug), Workflow, Board, Sprint, Filters |
| 18 | 🐙 **Git & GitHub** | Repository, commit, push, Markdown ilə QA sənədləşməsi, portfolio qurmaq |
| 19 | 💼 **Karyera hazırlığı** | CV, LinkedIn, GitHub portfolio, texniki müsahibə sualları |

</details>

---

## 🧰 Alətlər & Texnologiyalar

<p align="center">
  <img src="https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white"/>
  <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black"/>
  <img src="https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white"/>
  <img src="https://img.shields.io/badge/Chrome%20DevTools-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white"/>
  <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white"/>
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white"/>
  <img src="https://img.shields.io/badge/Windows%2011-0078D6?style=for-the-badge&logo=windows11&logoColor=white"/>
</p>

| Sahə | Alət |
|---|---|
| 📋 Test & Bug idarəetməsi | Jira, GitHub Markdown, Google Sheets |
| 🔌 API Testing | Postman, Swagger UI |
| 🌐 Web / UI Testing | Google Chrome, Chrome DevTools, Responsive (device) mode |
| 📱 Mobile Testing | Chrome Mobile (Android) |
| 🗄️ Data | SQL |
| 🐙 Versiya nəzarəti | Git, GitHub |
| ✍️ Sənədləşmə | Markdown, VS Code |

---

## 🗂️ Repozitoriyalar

| Repo | Layihə | Məzmun | Status |
|---|---|---|:-:|
| ⭐ [simplifaiapplicationtestcase](https://github.com/SemaEyvazli/simplifaiapplicationtestcase) | Smplifai | Test Plan · 11 test keys (UI + API) · Checklist · 3 Bug Report · Summary Report | ![](https://img.shields.io/badge/-complete-2EA44F?style=flat-square) |
| [testonline.az](https://github.com/SemaEyvazli/testonline.az) | OnlineTest | API Test Case — `taxonomy-service` | ![](https://img.shields.io/badge/-passed-2EA44F?style=flat-square) |
| [automation-exercise](https://github.com/SemaEyvazli/automation-exercise) | Automation Exercise | Exploratory testing · 3 Bug Report | ![](https://img.shields.io/badge/-open%20bugs-D73A49?style=flat-square) |

---

## 💪 Bacarıqlar — və sübutu

| Bacarıq | Harada tətbiq etmişəm |
|---|---|
| 🎯 **Test Design** (BVA, Negative, Error Guessing) | Səbətə `-1` məhsul, yanlış e-poçt formatı, çoxlu simvolla axtarış → [automation-exercise](https://github.com/SemaEyvazli/automation-exercise) |
| 🧪 **Test Case yazılması** | Tələb sənədinin bölmələrinə bağlı keyslər (`2.1`, `2.4`) → [testcase.md](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/testcase.md), [test-cases.md](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/test-cases.md) |
| 🔌 **API Testing** (Swagger, Postman, Bearer Token) | `POST 201`, `GET 200`, `DELETE 200`, `401`, `404` → [Smplifai API keysləri](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/application-delete-TC.md) |
| 🧩 **Mikroservis API testi** | API Gateway → `taxonomy-service` → `POST /api/v1/exam-definitions` → [testonline.az](https://github.com/SemaEyvazli/testonline.az) |
| 🐞 **Bug Reporting** (Severity / Priority) | 6 bug, hər birində Preconditions, Steps, Actual / Expected → [bugreport.md](https://github.com/SemaEyvazli/simplifaiapplicationtestcase/blob/main/bugreport.md) |
| 📱 **UI / Mobile testing** | Android Chrome-da responsive xəta (BUG-003, High) |
| 📝 **Test sənədləşməsi** | Test Plan → Checklist → Test Summary Report (tam STLC dövrü) |

---

## 🎯 Növbəti hədəflər

- [ ] Postman Collection + Environment ilə avtomatlaşdırılmış API test dəsti
- [ ] Postman `pm.test()` skriptləri ilə response validasiyası
- [ ] SQL ilə backend data yoxlaması (DB-level verification)
- [ ] QA Automation (Selenium / Playwright) öyrənmək
- [ ] ISTQB Foundation Level sertifikatı

---

## 📫 Əlaqə

<p align="center">
  <a href="https://github.com/SemaEyvazli"><img src="https://img.shields.io/badge/GitHub-SemaEyvazli-181717?style=for-the-badge&logo=github"/></a>
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=SemaEyvazli&theme=tokyo-night&hide_border=true&area=true" width="95%"/>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2C5364,50:203A43,100:0F2027&height=120&section=footer&animation=twinkling" alt="footer"/>
</p>
