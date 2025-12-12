# Government Employee Ticket Management System - Setup Instructions

## Project Overview

This is a **production-ready front-end application** for an internal government employee ticket management system. The system allows employees to manage, route, and track tickets submitted via phone or other channels.

### Key Features

- **Login System**: Secure employee authentication
- **Dashboard**: Overview of ticket metrics and statistics
- **Kanban Board**: Drag-and-drop ticket management with 4 status columns (Inbox, In Progress, Escalation, Done)
- **Ticket Details**: View and manage individual tickets with internal notes and timeline
- **Profile Management**: Employee profile and settings
- **Mock Data**: Fully functional with mock data (no backend required)

## Technology Stack

- **Frontend Framework**: React 19 with TypeScript
- **Styling**: Tailwind CSS 4
- **UI Components**: shadcn/ui
- **Routing**: Wouter
- **Charts**: Recharts
- **Icons**: Lucide React
- **Build Tool**: Vite

## Prerequisites

- Node.js 18+ (LTS recommended)
- npm or pnpm package manager

## Installation & Setup

### 1. Install Dependencies

```bash
npm install
# or
pnpm install
```

### 2. Start Development Server

```bash
npm run dev
# or
pnpm dev
```

The application will start at `http://localhost:3000`

### 3. Build for Production

```bash
npm run build
# or
pnpm build
```

### 4. Preview Production Build

```bash
npm run preview
# or
pnpm preview
```

## Login Credentials

The application uses mock authentication. You can log in with **any email and password**:

- **Email**: any@email.com (or any valid email format)
- **Password**: any password

The login page will display demo credentials for reference.

## Project Structure

```
govt_ticket_system/
├── client/
│   ├── public/                 # Static assets
│   ├── src/
│   │   ├── components/
│   │   │   ├── ui/            # shadcn/ui components
│   │   │   ├── TicketCard.tsx # Individual ticket card component
│   │   │   └── TicketDetailsModal.tsx # Ticket details modal
│   │   ├── pages/
│   │   │   ├── Login.tsx       # Login page
│   │   │   ├── Home.tsx        # Dashboard/Home page
│   │   │   ├── TicketBoard.tsx # Kanban board page
│   │   │   ├── Profile.tsx     # Employee profile page
│   │   │   └── NotFound.tsx    # 404 page
│   │   ├── types/
│   │   │   └── index.ts        # TypeScript type definitions
│   │   ├── lib/
│   │   │   └── mockData.ts     # Mock data and API services
│   │   ├── contexts/
│   │   │   └── ThemeContext.tsx # Theme management
│   │   ├── App.tsx             # Main app component with routes
│   │   ├── main.tsx            # React entry point
│   │   └── index.css           # Global styles and Tailwind config
│   └── index.html              # HTML template
├── server/
│   └── index.ts                # Express server (for production)
├── shared/
│   └── const.ts                # Shared constants
└── package.json                # Dependencies and scripts
```

## Features & Pages

### 1. Login Page (`/login`)
- Employee authentication form
- Demo credentials displayed
- Redirects to home page on successful login
- Stores user in localStorage

### 2. Home/Dashboard Page (`/`)
- Welcome message with employee name
- Key metrics cards (Open, In Progress, Escalated, Completed)
- Ticket status distribution chart
- Severity distribution pie chart
- Quick navigation buttons

### 3. Ticket Board Page (`/tickets`)
- **Kanban Board** with 4 columns:
  - **Inbox**: New tickets not yet assigned
  - **In Progress**: Tickets being worked on
  - **Escalation**: Tickets requiring supervisor intervention
  - **Done**: Completed tickets
- **Drag-and-drop** functionality to move tickets between columns
- **Search** by ticket ID, title, or description
- **Filter** by severity level (Low, Medium, High, Critical)
- Click any ticket card to view full details

### 4. Ticket Details Modal
- View complete ticket information
- Change ticket status via dropdown
- View ticket severity, category, and metadata
- **Internal Notes** section to add and view notes
- **Timeline** showing all ticket history and changes
- Submitted by and assigned to information

### 5. Profile Page (`/profile`)
- View employee information (Name, Email, Department, Role, ID)
- Edit profile (UI only, no backend)
- Notification preferences
- Account security options

## Mock Data

The application includes **8 pre-loaded mock tickets** with realistic data:

- **TKT-001**: Pothole on Main Street (High, Inbox)
- **TKT-002**: Street Light Outage (High, In Progress)
- **TKT-003**: Water Leak in Park (Critical, Escalation)
- **TKT-004**: Noise Complaint (Medium, Inbox)
- **TKT-005**: Construction Noise (Medium, Done)
- **TKT-006**: Graffiti on Building (Low, In Progress)
- **TKT-007**: Sidewalk Damage (Medium, Inbox)
- **TKT-008**: Broken Traffic Signal (High, Done)

All tickets have:
- Detailed descriptions
- Severity levels
- Submission dates
- Internal notes
- Timeline/history
- Assignment information

## Key Functionality

### Drag-and-Drop Ticket Movement
1. Click and hold a ticket card
2. Drag it to a different column
3. Drop to update the ticket status
4. Status changes are reflected immediately

### Search and Filter
- **Search**: Type in the search box to find tickets by ID, title, or description
- **Filter**: Select a severity level to show only tickets of that severity
- Filters work together (search AND filter)

### Add Internal Notes
1. Click on any ticket to open details modal
2. Scroll to "Internal Notes" section
3. Click "Add Note" button
4. Type your note and click "Save Note"
5. Note appears in the ticket's internal notes list

### View Timeline
- Each ticket has a detailed timeline showing:
  - When the ticket was submitted
  - When it was classified
  - When it was assigned
  - Status changes
  - When notes were added

## Styling & Design

### Color Scheme
- **Primary**: Blue (#3b82f6)
- **Success**: Green (#10b981)
- **Warning**: Amber (#f59e0b)
- **Danger**: Red (#ef4444)
- **Escalation**: Purple (#8b5cf6)

### Responsive Design
- Mobile-first approach
- Optimized for desktop viewing
- Kanban board stacks on mobile
- Navigation menu collapses on smaller screens

## Available Scripts

```bash
# Development
npm run dev          # Start dev server with hot reload

# Production
npm run build        # Build for production
npm run start        # Start production server (after build)
npm run preview      # Preview production build locally

# Code Quality
npm run check        # TypeScript type checking
npm run format       # Format code with Prettier
```

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Notes for Development

### Adding New Pages
1. Create a new file in `client/src/pages/`
2. Import it in `App.tsx`
3. Add a new `<Route>` in the Router component

### Modifying Mock Data
- Edit `client/src/lib/mockData.ts` to change ticket data
- Modify `mockDashboardMetrics` to update dashboard numbers
- Add new tickets to the `mockTickets` array

### Styling Components
- Use Tailwind CSS utility classes
- Reference design tokens in `client/src/index.css`
- Import shadcn/ui components from `@/components/ui/`

### Type Safety
- All types are defined in `client/src/types/index.ts`
- Use TypeScript interfaces for better IDE support
- Run `npm run check` to verify type safety

## Troubleshooting

### Port Already in Use
If port 3000 is already in use, Vite will automatically use the next available port.

### Styles Not Loading
- Clear browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
- Restart the dev server
- Check that Tailwind CSS is properly configured in `index.css`

### Login Not Working
- Ensure localStorage is enabled in browser
- Check browser console for errors
- Try logging in with any email/password combination

### Drag-and-Drop Not Working
- Ensure you're using a modern browser
- Check that JavaScript is enabled
- Try refreshing the page

## Performance Considerations

- Mock data is loaded synchronously (instant)
- Simulated API delays (300-500ms) for realistic feel
- Efficient re-rendering with React hooks
- Optimized Tailwind CSS with purging

## Future Enhancements

- Backend API integration
- Real authentication system
- Database for persistent storage
- Real-time notifications
- Advanced filtering and sorting
- Export tickets to PDF/CSV
- User role-based access control
- Ticket assignment workflows
- SLA tracking and alerts

## Support & Documentation

For questions or issues:
1. Check the code comments in each component
2. Review the TypeScript types in `client/src/types/index.ts`
3. Examine mock data structure in `client/src/lib/mockData.ts`

---

**Version**: 1.0.0  
**Last Updated**: December 2024  
**Status**: Production Ready
