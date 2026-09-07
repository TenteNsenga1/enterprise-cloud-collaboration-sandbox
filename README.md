# ☁️ Enterprise Cloud Collaboration Sandbox

**Project Overview:** A local, containerized groupware platform simulating enterprise collaboration, document governance, and scheduling infrastructure. Built with **Nextcloud Hub** as an open-source equivalent to practice **SharePoint Online** and **Exchange Online (calendar/resource) administration** workflows — companion project to my [Keycloak IAM sandbox](https://github.com/TenteNsenga1/enterprise-iam-sandbox).

\---

### 🛠️ Core Infrastructure Stack

* **Collaboration Platform:** Nextcloud Hub
* **Containerization \& Runtime:** Docker Engine (WSL 2 on Windows 11)
* **Key Apps:** Team Folders (Group folders), Calendar, Calendar Resource Management, Contacts

\---

### 💼 Technical Skill Mapping (M365 Equivalent)

|Implemented Nextcloud Feature|Microsoft 365 Equivalent|Business \& Security Value|
|-|-|-|
|**Team Folders (Group Folders)**|SharePoint Online Document Libraries|Department-scoped storage with admin-managed, group-based permissions.|
|**Group-based read/write vs. read-only shares**|SharePoint permission levels / RBAC|Enforces the Principle of Least Privilege across departments.|
|**Shared Calendars (CalDAV)**|Exchange Online shared calendars|Cross-team visibility into schedules without exposing full mailbox access.|
|**Calendar Resource Management**|Exchange Online room/resource mailboxes|Centralized, conflict-aware booking of shared physical resources (meeting rooms).|
|**Contacts (CardDAV)**|Exchange Global Address List|Centralized, shared organizational directory.|
|**Activity \& file version history**|M365 Purview / version history|Auditability of who changed what, when.|

*Note: Nextcloud's Mail app is an IMAP/SMTP **client** (like Outlook), not a mailbox-hosting server like Exchange — this lab focuses on the calendar, resource-booking, and file-governance features that map most directly to hands-on Microsoft 365 admin tasks, rather than claiming mailbox hosting it doesn't do.*

\---

### 📂 Key Lab Accomplishments

* **Departmental Access Governance:** Created a group-scoped `Active-Trial-Protocols` folder giving the `Clinical-Trials` group read/write access while `IT-Support` retains read-only visibility — replicating SharePoint document library permission structures in a regulated (clinical research) context.

  !\[Team Folders permission structure](team-folders.png)

* **Shared Scheduling \& Resource Booking:** Configured a shared team calendar with tiered edit/view permissions across test users, and registered a bookable meeting-room resource with automatic conflict detection — replicating Exchange Online resource-mailbox scheduling.

  !\[Calendar sharing and resource booking](calendar-resource.png)

* **Organizational Directory:** Enabled a shared Contacts address book to simulate a centralized company directory (Global Address List equivalent).

\---

## 🚀 How to Run the Environment

```powershell
docker run -d --name nextcloud-sandbox -p 8081:80 -v nextcloud\_data:/var/www/html nextcloud:stable
```

Then visit `http://localhost:8081` and complete the admin setup wizard.

\---

## 🔗 Related Project

[enterprise-iam-sandbox](https://github.com/TenteNsenga1/enterprise-iam-sandbox) — Keycloak-based Identity \& Access Management lab (Entra ID equivalent).

