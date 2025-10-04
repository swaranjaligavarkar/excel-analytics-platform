# Excel Analytics Platform – Design Format

## 1. Project Structure

```
excel-analytics-platform/
├── backend/
│   ├── models/
│   ├── routes/
│   ├── controllers/        # (for separating logic)
│   ├── middleware/         # (for JWT auth etc.)
│   ├── uploads/            # (for storing files)
│   └── server.js
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── store/
│       ├── App.js
│       ├── index.js
│       └── tailwind.css
├── README.md
└── DESIGN.md
```

## 2. User Flow

### 2.1 Authentication
- **Register** (username, password, role)
- **Login** (returns JWT token)
- **Admin/User Dashboard**

### 2.2 Upload & Analysis
- User uploads Excel file (.xls/.xlsx)
- Backend parses file, returns columns and raw data
- User selects X/Y axes from columns
- User selects chart type (2D/3D)
- Chart is rendered (Chart.js/Three.js)
- User can download chart (PNG/PDF)
- Upload/analysis history saved per user

### 2.3 Admin Features
- Admin can view users
- Admin can manage uploads/data usage

### 2.4 Optional AI Insights
- AI API endpoint for summary/insights from uploaded Excel data

## 3. Backend Design

- **Express.js API**  
  - /api/auth/register  
  - /api/auth/login  
  - /api/files/upload  
  - /api/files/history  
  - /api/chart/generate (optional)  
  - /api/ai/summary (optional)  
  - /api/admin/users (admin only)  

- **MongoDB Models**  
  - User  
  - Upload (file name, user, columns, date, etc.)  
  - Analysis (user, chart config, summary, etc.)

- **Middleware**  
  - JWT authentication  
  - Role-based access (admin/user)

## 4. Frontend Design

- **React Pages**
  - Login/Register
  - Dashboard (file upload, history, chart view)
  - Admin Panel (user management)
  - Analysis Details (show chart, summary)

- **UI Libraries**
  - Tailwind CSS (layout, styling)
  - Chart.js (2D charts)
  - Three.js (3D charts)
  - html2canvas or similar (chart download)

- **State Management**
  - Redux Toolkit

## 5. Feature Modules (Week-wise)

| Week | Module Description                   |
|------|--------------------------------------|
| 1    | Setup project, user/admin auth, dashboard layout         |
| 2    | File upload, Excel parsing, MongoDB storage              |
| 3    | Chart rendering, dynamic axes, chart selection           |
| 4    | History, download feature, AI summary                    |
| 5    | Admin panel, testing, deployment                         |

## 6. References

- [SheetJS](https://sheetjs.com/)
- [Chart.js](https://www.chartjs.org/)
- [Three.js](https://threejs.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [MongoDB Atlas](https://www.mongodb.com/atlas)
- [Render](https://render.com/)
- [Netlify](https://www.netlify.com/)

## 7. UI Wireframe Example

```
+------------------------------------------+
|           Login/Register Page            |
+------------------------------------------+

+------------------------------------------+
|               Dashboard                  |
| [Upload Excel File]                      |
| [History Table]  [Chart View]            |
| [Download Chart] [AI Summary]            |
+------------------------------------------+

+------------------------------------------+
|               Admin Panel                |
| [User List] [Manage Users] [Usage Stats] |
+------------------------------------------+
```