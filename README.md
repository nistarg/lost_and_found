# Campus Lost & Found Management System

A production-ready web application for managing lost and found items on campus. Built with Express.js backend, vanilla JavaScript frontend, and file-based JSON database.

## Features

✨ **User Authentication**
- Secure registration and login with JWT tokens
- Password hashing with bcryptjs
- Protected routes and API endpoints

📝 **Item Management**
- Report lost items with details and images
- Report found items to help others
- Upload and optimize images (auto-resize to 800x800)
- Edit and delete your own items

🔍 **Search & Filter**
- Search by keywords, category, location
- Filter by item type (lost/found) and status
- Real-time statistics dashboard
- Recent items display on homepage

👤 **User Dashboard**
- View all your reported items
- Manage item status
- Track claims and returns

🔒 **Security Features**
- Helmet.js for HTTP headers
- Rate limiting on API endpoints
- Input validation with express-validator
- CORS protection
- JWT token expiration

## Tech Stack

**Backend:**
- Node.js & Express.js
- JWT authentication
- Bcrypt password hashing
- Multer & Sharp for image processing
- Express-validator for validation
- File-based JSON database

**Frontend:**
- Vanilla JavaScript (no framework dependencies)
- Responsive CSS Grid & Flexbox
- Fetch API for AJAX requests
- localStorage for auth persistence

## Installation

1. **Clone or download the project**

2. **Install dependencies:**
```bash
npm install
```

3. **Create environment file:**
```bash
cp .env.example .env
```

4. **Edit `.env` and change the JWT_SECRET:**
```env
JWT_SECRET=your-actual-secret-key-here
PORT=3000
NODE_ENV=development
```

5. **Start the server:**

**Development mode (with auto-reload):**
```bash
npm run dev
```

**Production mode:**
```bash
npm start
```

6. **Open your browser:**
Navigate to `http://localhost:3000`

## Project Structure

```
lost-and-found/
├── database/
│   ├── db.js              # Database layer
│   └── data/              # JSON data files (auto-created)
│       ├── users.json
│       ├── items.json
│       └── claims.json
├── routes/
│   ├── auth.js            # Authentication routes
│   ├── items.js           # Items CRUD routes
│   ├── claims.js          # Claims management
│   ├── users.js           # User profile routes
│   └── stats.js           # Statistics API
├── middleware/
│   └── auth.js            # JWT authentication middleware
├── uploads/               # User-uploaded images (auto-created)
├── server.js              # Express server setup
├── app.js                 # Frontend JavaScript utilities
├── styles.css             # Shared stylesheet
├── index.html             # Landing page
├── login.html             # Login page
├── register.html          # Registration page
├── dashboard.html         # User dashboard
├── report-lost.html       # Report lost item form
├── report-found.html      # Report found item form
├── search.html            # Search & browse items
├── package.json           # Dependencies
├── .env.example           # Environment template
└── README.md              # This file
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Items
- `GET /api/items` - Get all items (with filters)
- `GET /api/items/:id` - Get single item
- `POST /api/items` - Create new item (auth required)
- `PUT /api/items/:id` - Update item (auth required)
- `DELETE /api/items/:id` - Delete item (auth required)
- `GET /api/items/user/my-items` - Get user's items (auth required)

### Users
- `GET /api/users/me` - Get current user profile (auth required)
- `PUT /api/users/me` - Update user profile (auth required)

### Claims
- `GET /api/claims/item/:itemId` - Get claims for item (auth required)
- `GET /api/claims/my-claims` - Get user's claims (auth required)
- `POST /api/claims` - Create claim (auth required)
- `PUT /api/claims/:id` - Update claim status (auth required)

### Statistics
- `GET /api/stats` - Get portal statistics

## Usage Guide

### For Students

1. **Register an account** using your email
2. **Report a lost item:**
   - Click "Report Lost Item"
   - Fill in details, upload image
   - Submit
3. **Report a found item:**
   - Click "Report Found Item"
   - Provide details to help owner identify
   - Submit
4. **Search for items:**
   - Use search page to filter by category, location, type
   - View contact info to coordinate return

### For Admins

The system currently uses a flat user structure. For admin features, you can:
- Extend the user model with a `role` field
- Add middleware to check for admin role
- Create admin routes for managing all items and users

## Development

### Running Tests (Optional - Setup Required)
```bash
npm test
```

### Linting (Optional - Setup Required)
```bash
npm run lint
```

### Database Backup
The database is stored in `database/data/` as JSON files. To backup:
```bash
# Create backup directory
mkdir backups

# Copy data files
cp database/data/*.json backups/
```

## Security Considerations

⚠️ **Important for Production:**

1. **Change JWT_SECRET** in `.env` to a strong random string
2. **Use HTTPS** in production (configure reverse proxy)
3. **Set NODE_ENV=production**
4. **Configure proper CORS** origins in server.js
5. **Add rate limiting** for auth endpoints
6. **Regular backups** of database files
7. **File upload size limits** are set to 5MB
8. **Image validation** - only jpeg, jpg, png, gif, webp allowed

## Troubleshooting

**Server won't start:**
- Check if port 3000 is available
- Verify all dependencies are installed: `npm install`

**Images not uploading:**
- Check uploads directory exists and is writable
- Verify file size is under 5MB
- Ensure image format is supported

**Authentication errors:**
- Clear browser localStorage
- Check JWT_SECRET is set in .env
- Verify token hasn't expired (7 day default)

**Database errors:**
- Ensure `database/data/` directory exists
- Check file permissions
- Verify JSON files are valid

## Future Enhancements

- Email notifications for matches
- Admin dashboard
- Advanced search with date ranges
- Item claiming workflow
- Multi-language support
- Real-time updates with WebSockets
- Mobile app version
- Integration with campus ID system

## License

MIT License - Free to use and modify

## Support

For issues or questions, please contact your campus IT department or create an issue in the project repository.

---

**Made with ❤️ for Campus Community**
