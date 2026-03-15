<div align="center">
  <img src="./Assets/thing.png" width="700"/>
</div>

<h1>thing.</h1>

<p>
  <strong>thing</strong> is a mobile e-commerce application designed for buying and selling
  high-quality furniture products such as cupboards, chairs, tables, and other home furniture items.
</p>

<p>
  The application connects customers who are looking for modern and quality furniture
  with merchants who want to expand their market and offer their products online.
</p>

<p>
  <strong>thing</strong> provides a simple, clean, and user-friendly shopping experience
  while enabling sellers to manage their products and orders efficiently.
</p>

<div align="center">

<table>
<tr>
<td align="center" width="900" style="padding:22px 40px; border:1px solid #e5e5e5; border-radius:12px;">

<br/>

<div align="center">
  <img src="./Assets/logo.gif" width="700"/>
</div>

<br/>

<h2 style="letter-spacing:2px; font-weight:600; color:#444;">
OUR PHILOSOPHY
</h2>

<br/>

<h3>
<em>
"Furniture may be just a <strong>thing</strong> — but it's <strong>the thing.</strong> that turns a house into a home."
</em>
</h3>

<br/>

</td>
</tr>
</table>

</div>

<br/>

<div align="center">

![Android](https://img.shields.io/badge/Android-3DDC84?style=flat&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat&logo=kotlin&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat&logo=firebase&logoColor=black)
![Min SDK](https://img.shields.io/badge/Min_SDK-24-4A90E2?style=flat&logo=android&logoColor=white)
![MVVM](https://img.shields.io/badge/MVVM-Architecture-4A90E2?style=flat)
![Status](https://img.shields.io/badge/Status-In_Development-E67E22?style=flat)

</div>

<br/>

---

## Team Details

| &nbsp; | Name | Student ID | GitHub |
|:------:|:-----|:----------:|:-------|
| <img src="https://github.com/samedTevin.png" width="65" height="65" style="border-radius:50%"/> | **Samed Tevin** | 230513327 | [![GitHub](https://img.shields.io/badge/GitHub-samedTevin-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/samedTevin) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/samedtevin/) |
| <img src="https://github.com/hasanackl.png" width="65" height="65" style="border-radius:50%"/> | **Hasan Açıkel** | 220513343 | [![GitHub](https://img.shields.io/badge/GitHub-hasanackl-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/hasanackl) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hasana%C3%A7%C4%B1kel/) |
| <img src="https://github.com/CoderRoninn.png" width="65" height="65" style="border-radius:50%"/> | **Doğukan Süme** | 210513243 | [![GitHub](https://img.shields.io/badge/GitHub-CoderRoninn-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/CoderRoninn) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dogukansume/) |
| <img src="https://github.com/KaganxSahin.png" width="65" height="65" style="border-radius:50%"/> | **Kağan Şahin** | 220513375 | [![GitHub](https://img.shields.io/badge/GitHub-KaganxSahin-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/KaganxSahin) [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kaganxsahin/) |

---

## Project Introduction

**thing.** is an Android mobile application built with Kotlin and Firebase that serves as a marketplace for home furniture. It addresses the gap between quality furniture sellers and buyers by providing a seamless platform where:

- **Buyers** can browse, search, filter, and purchase furniture with a clean and intuitive UI.
- **Sellers** can list, manage, and track their products and orders through a dedicated dashboard.

The app follows the **MVVM** architecture pattern with Firebase as the backend (Authentication, Firestore, Storage), and uses Hilt for dependency injection and Kotlin Coroutines for async operations.

---

## Architecture Link

📐 Full architecture documentation: [ARCHITECTURE.md](./ARCHITECTURE.md)

---

<details open>
  <summary><h2>Documents</h2></summary>

| Document | File |
|:---------|:-----|
| 📋 Project Proposal | [SWE332_Project_Proposal.pdf](./ProjectManagement/Documents/SWE332_Project_Proposal.pdf) |
| 👤 Persona File | [thingPersonaFile.pdf](./ProjectManagement/Documents/thingPersonaFile.pdf) |

</details>

---

## Navigation Flow

```mermaid
graph TD
    A([Splash]) --> B{Authenticated?}
    B -- No --> C[Login / Register]
    B -- Yes --> D[Home Feed]
    C --> D
    D --> E[Product Detail]
    D --> F[Search & Filter]
    D --> G[Categories]
    E --> H[Cart]
    H --> I[Checkout]
    I --> J[Order Confirmation]
    D --> K[Seller Dashboard]
    K --> L[Add / Edit Product]
    K --> M[Order Management]

    style A fill:#3DDC84,color:#000
    style B fill:#FFCA28,color:#000
    style D fill:#7F52FF,color:#fff
    style H fill:#F05032,color:#fff
    style I fill:#F05032,color:#fff
    style J fill:#27AE60,color:#fff
    style K fill:#FFA000,color:#000
```

---

<details>
  <summary><h2>Architecture Overview</h2></summary>

**thing.** follows **MVVM (Model-View-ViewModel)** for clean separation of concerns and testability.

```mermaid
flowchart TD
    subgraph UI["UI Layer"]
        F[Fragments]
        A[Activities]
        AD[Adapters]
    end
    subgraph VM["ViewModel Layer"]
        VML[ViewModels]
        LD[LiveData]
    end
    subgraph REPO["Repository Layer"]
        R[Repository]
    end
    subgraph DI["DI Layer"]
        H[Hilt Modules]
    end
    subgraph FIREBASE["Firebase"]
        AUTH[Firebase Auth]
        FS[Firestore]
        ST[Storage]
    end
    UI -->|observes| VM
    VM -->|calls| REPO
    REPO --> AUTH
    REPO --> FS
    REPO --> ST
    DI -->|injects| VM
    DI -->|injects| REPO
```

</details>

---

# Sprints

<div align="center">
  <img src="./Assets/sprints.png" width="700"/>
</div>

---

<details>
  <summary><h1>Sprint 1</h1></summary>

---

<details>
    <summary><h2>App Screenshots</h2></summary>

Coming Soon.

New features and updated screens will be added in this section.

</details>

---

<details>
  <summary><h2>Project Management</h2></summary>

Coming Soon.

Sprint board visuals and task distribution details will be shared here.

</details>

---

<details>
  <summary><h2>Burndown Chart</h2></summary>

Coming Soon.

Sprint burndown and performance charts will be available here.

</details>

---

- **Sprint Notes:**
  * To be updated.

- **Expected point completion within Sprint:**
  * `TBA`

- **Point Completion Logic:**
  * Details will be updated at the end of the sprint.

- **Sprint Review:**
  * To be updated.

- **Sprint Review Participants:**
  * `TBA`

- **Sprint Retrospective:**
  * To be updated.

</details>

---

<details>
  <summary><h1>Sprint 2</h1></summary>

---

<details>
    <summary><h2>App Screenshots</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Project Management</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Burndown Chart</h2></summary>

Coming Soon.

</details>

---

- **Sprint Notes:** To be updated.
- **Expected point completion within Sprint:** `TBA`
- **Point Completion Logic:** Details will be updated at the end of the sprint.
- **Sprint Review:** To be updated.
- **Sprint Review Participants:** `TBA`
- **Sprint Retrospective:** To be updated.

</details>

---

<details>
  <summary><h1>Sprint 3</h1></summary>

---

<details>
    <summary><h2>App Screenshots</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Project Management</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Burndown Chart</h2></summary>

Coming Soon.

</details>

---

- **Sprint Notes:** To be updated.
- **Expected point completion within Sprint:** `TBA`
- **Point Completion Logic:** Details will be updated at the end of the sprint.
- **Sprint Review:** To be updated.
- **Sprint Review Participants:** `TBA`
- **Sprint Retrospective:** To be updated.

</details>

---

<details>
  <summary><h1>Sprint 4</h1></summary>

---

<details>
    <summary><h2>App Screenshots</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Project Management</h2></summary>

Coming Soon.

</details>

---

<details>
  <summary><h2>Burndown Chart</h2></summary>

Coming Soon.

</details>

---

- **Sprint Notes:** To be updated.
- **Expected point completion within Sprint:** `TBA`
- **Point Completion Logic:** Details will be updated at the end of the sprint.
- **Sprint Review:** To be updated.
- **Sprint Review Participants:** `TBA`
- **Sprint Retrospective:** To be updated.

</details>

---

# Endnotes

<div align="center">
 <img src="./Assets/endnotes.png" width="700"/>
</div>

---

## thing. Promo

### Video

<p align="center"><em>Coming Soon.</em></p>

---

<details open>
  <summary><h2>Tech Stack</h2></summary>

### Libraries & Technologies

| Category | Technologies |
|----------|-------------|
| Language | ![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat&logo=kotlin&logoColor=white) |
| Architecture | ![MVVM](https://img.shields.io/badge/MVVM-4A90E2?style=flat) ![LiveData](https://img.shields.io/badge/LiveData-1E88E5?style=flat) ![Navigation](https://img.shields.io/badge/Navigation_Component-3949AB?style=flat) |
| Backend | ![Firebase Auth](https://img.shields.io/badge/Firebase_Auth-FFCA28?style=flat&logo=firebase&logoColor=black) ![Firestore](https://img.shields.io/badge/Firestore-FFA000?style=flat&logo=firebase&logoColor=black) ![Firebase Storage](https://img.shields.io/badge/Firebase_Storage-F57C00?style=flat&logo=firebase&logoColor=black) |
| Concurrency | ![Coroutines](https://img.shields.io/badge/Kotlin_Coroutines-7F52FF?style=flat&logo=kotlin&logoColor=white) |
| Dependency Injection | ![Hilt](https://img.shields.io/badge/Hilt-DI-E91E63?style=flat&logo=android&logoColor=white) |
| UI | ![View Binding](https://img.shields.io/badge/View_Binding-43A047?style=flat&logo=android&logoColor=white) ![Glide](https://img.shields.io/badge/Glide-2E7D32?style=flat) |
| Design | ![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat&logo=figma&logoColor=white) |
| Tools | ![Android Studio](https://img.shields.io/badge/Android_Studio-3DDC84?style=flat&logo=android-studio&logoColor=white) |
| Version Control | ![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white) |
| Project Management | ![Jira](https://img.shields.io/badge/Jira-0052CC?style=flat&logo=jira&logoColor=white) |

</details>

---

<details open>
  <summary><h2>Design</h2></summary>

### Font

| Weight | File |
|--------|------|
| Bold | `inter_18pt_bold.ttf` |
| SemiBold | `inter_18pt_semibold.ttf` |
| Medium | `inter_18pt_medium.ttf` |
| Regular | `inter_18pt_regular.ttf` |

### Colors

| Name | Hex | Preview |
|------|-----|---------|
| Black | `#171717` | ![](https://img.shields.io/badge/-%23171717-171717) |
| White | `#F5F8FA` | ![](https://img.shields.io/badge/-%23F5F8FA-F5F8FA) |
| Blue | `#000DAE` | ![](https://img.shields.io/badge/-%23000DAE-000DAE) |
| Dark Blue | `#000759` | ![](https://img.shields.io/badge/-%23000759-000759) |
| Blue Gray | `#97AABD` | ![](https://img.shields.io/badge/-%2397AABD-97AABD) |
| Blue 100 | `#B8D9FA` | ![](https://img.shields.io/badge/-%23B8D9FA-B8D9FA) |
| Gray 500 | `#969899` | ![](https://img.shields.io/badge/-%23969899-969899) |
| Gray 700 | `#666666` | ![](https://img.shields.io/badge/-%23666666-666666) |
| Light Red | `#FF9999` | ![](https://img.shields.io/badge/-%23FF9999-FF9999) |
| Red | `#FF0000` | ![](https://img.shields.io/badge/-%23FF0000-FF0000) |
| Orange Yellow | `#F8BA00` | ![](https://img.shields.io/badge/-%23F8BA00-F8BA00) |
| Card Background | `#FAFDFF` | ![](https://img.shields.io/badge/-%23FAFDFF-FAFDFF) |
| Line | `#E9EAEC` | ![](https://img.shields.io/badge/-%23E9EAEC-E9EAEC) |

</details>

---
