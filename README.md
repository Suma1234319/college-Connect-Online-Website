# College Connect - Unified Communication Platform

A comprehensive college management system with hierarchical access control and real-time communication features.

## 🏛️ System Overview

College Connect is a unified communication platform designed for educational institutions, providing role-based access control and department-specific communication channels.

## 🔐 Authentication & Access Control

### Hierarchical Authority System
- **Super Admin (Suma)** 🛡️ - Master system control
- **College Management** 🏛️ - College-wide authority  
- **Department Admins** 👨‍💼 - Department-specific control
- **Faculty & Students** 👨‍🏫👨‍🎓 - End users

### Real-time Password Reset
- Direct email delivery to user's email address
- Secure token-based reset system
- 1-hour expiration for security
- Professional email templates

## 📧 Email Service Integration

### Real-time Email OTP Setup (EmailJS)
1. Create account at [EmailJS](https://www.emailjs.com/)
2. Set up email service (Gmail, Outlook, etc.)
3. Create email template for OTP password reset
4. Update configuration in `.env` file:

```env
VITE_EMAILJS_SERVICE_ID=your_service_id
VITE_EMAILJS_TEMPLATE_ID=your_template_id
VITE_EMAILJS_PUBLIC_KEY=your_public_key
```

### Email OTP Template Variables
- `{{to_email}}` - Recipient email address
- `{{to_name}}` - User's name
- `{{otp_code}}` - 6-digit OTP code
- `{{college_name}}` - Institution name
- `{{expiry_time}}` - OTP expiration time (10 minutes)
- `{{support_email}}` - Support contact email

### Sample Email Template
```
Subject: Password Reset OTP - College Connect

Dear {{to_name}},

Your password reset OTP for College Connect is:

**{{otp_code}}**

This OTP will expire in {{expiry_time}}.

If you did not request this, please ignore this email.

Best regards,
{{college_name}} IT Team
```

## 🚀 Features

### Core Functionality
- **Role-based Dashboards** - Customized interfaces for each user type
- **Department Management** - Hierarchical approval system
- **Real-time Notifications** - Instant updates and alerts
- **Secure Authentication** - Multi-level access control

### Communication Tools
- **Announcements** - Department and college-wide messaging
- **Faculty Status** - Availability tracking
- **Exam Schedules** - Centralized exam management
- **Fee Information** - Payment tracking and notifications
- **Holiday Calendar** - Academic calendar management

### Administrative Features
- **User Approval System** - Hierarchical request approval
- **Department Creation** - Dynamic department management
- **Branch Management** - Academic branch organization
- **Audit Trail** - Complete activity logging

## 🛠️ Technical Requirements

### Software Requirements
- **Frontend**: React.js 18+ with TypeScript
- **Styling**: Tailwind CSS 3.4+
- **Icons**: Lucide React
- **Email Service**: EmailJS or custom backend
- **Storage**: LocalStorage (demo) / Database (production)
- **Runtime**: Node.js 18+ Environment

### Hardware Requirements
- **Development**: PC/Laptop with 4GB+ RAM
- **Production Server**: 2GB+ RAM, 10GB+ storage
- **Client Access**: Any device with web browser
- **Network**: Stable internet connection

### Browser Support
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## 📱 Responsive Design
- Mobile-first approach
- Tablet optimization
- Desktop enhancement
- Cross-platform compatibility

## 🔒 Security Features

### Authentication Security
- Secure password hashing
- Token-based reset system
- Session management
- Role-based access control

### Data Protection
- Input validation
- XSS prevention
- CSRF protection
- Secure communication

## 🎨 Design System

### Color Palette
- **Primary**: Blue (#3B82F6)
- **Secondary**: Purple (#8B5CF6)
- **Success**: Green (#10B981)
- **Warning**: Yellow (#F59E0B)
- **Error**: Red (#EF4444)

### Typography
- **Headings**: Inter Bold
- **Body**: Inter Regular
- **Code**: JetBrains Mono

## 📊 User Roles & Permissions

## 🔒 Strict Hierarchical Access Control System

| Hierarchy Level | Role | Can Approve | Authority Scope | System Access |
|----------------|------|-------------|-----------------|---------------|
| **Level 1** | Super Admin | College Management & Department Admins ONLY | System-wide | Full System Control |
| **Level 2** | College Management | Department Admins ONLY | College-wide | College Policies & Announcements |
| **Level 3** | Department Admin | Faculty & Students in their departments ONLY | Department-specific | Department Management |
| **Level 4** | Faculty | Students in their department ONLY | Student Management | Limited Department Access |
| **Level 5** | Student | None | Personal Access | View-only Access |

### 🛡️ Hierarchy Rules:
- **Strict One-Level-Down Rule**: Each level can ONLY approve the immediate level below
- **No Skip-Level Approvals**: Super Admin cannot directly approve Students
- **Department Boundaries**: Department Admins and Faculty can only manage users in their assigned departments

## 🚀 Getting Started

### Development Setup
```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

### Default Login Credentials

#### Super Admin
- Email: `admin@college.edu`
- Password: `admin123`

#### College Management
- Email: `college@college.edu`
- Password: `college123`

#### Department Management
- Email: `mca@college.edu`
- Password: `mca123`

#### Faculty
- Email: `faculty1@college.edu`
- Password: `faculty123`

#### Student
- Email: `student1@college.edu`
- Password: `student123`

## 📈 Scalability

### Performance Optimization
- Component lazy loading
- Image optimization
- Code splitting
- Caching strategies

### Database Scaling
- Indexed queries
- Connection pooling
- Read replicas
- Horizontal scaling

## 🔧 Configuration

### Environment Variables
```env
VITE_EMAIL_SERVICE_ID=your_emailjs_service_id
VITE_EMAIL_TEMPLATE_ID=your_emailjs_template_id  
VITE_EMAIL_PUBLIC_KEY=your_emailjs_public_key
VITE_API_BASE_URL=your_backend_api_url
```

### Deployment Options
- **Netlify** - Frontend hosting
- **Vercel** - Full-stack deployment
- **AWS** - Enterprise scaling
- **Docker** - Containerized deployment

## 📞 Support

### Technical Support
- Email: support@collegeconnect.edu
- Phone: +91-XXXX-XXXXXX
- Documentation: [docs.collegeconnect.edu]

### Development Team
- **Lead Developer**: Suma Technology Solutions
- **UI/UX Design**: Modern responsive design
- **Backend Architecture**: Scalable microservices
- **Security**: Enterprise-grade protection

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 🧪 **Test the Fixed Flow:**

### **Real-time Email OTP Test:**
1. **Click "Forgot Password"** on any login page
2. **Enter email address** → Real OTP sent to actual email
3. **Check email inbox** → Receive 6-digit OTP code
4. **Enter OTP + new password** → Password reset successfully
5. **Login with new password** → Success!

### **Student Registration Test:**
1. **Register as Student** → Request goes to **Faculty** (not admin)
2. **Login as Faculty** (`faculty1@college.edu` / `faculty123`)

---

**College Connect v1.0** - Empowering Educational Communication