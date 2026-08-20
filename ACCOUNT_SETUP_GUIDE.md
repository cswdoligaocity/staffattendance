# Employee Account Setup — CSWDO QR Logbook

## What is already included
All 35 employees are already in `public.employees` as employee records.

Examples:
- CSWDO-01 — IRENE BARBERO-RACHO
- CSWDO-14 — CELITO JOE PERILLO
- CSWDO-35 — ADELINA CASADA

These are NOT login accounts yet.

## New Admin feature
After deployment, the Admin Dashboard has:
**Create Employee Account**

The admin selects an employee, enters:
- Employee email
- Temporary password

Then clicks **Create Account**.

The system securely calls the Supabase Edge Function. The Edge Function:
1. Verifies the caller is an Admin.
2. Creates the Supabase Auth account.
3. Confirms the email for the account (because the office is creating the account).
4. Automatically links the Auth user to the selected employee.
5. Gives the employee access to the QR attendance system.

## Required Edge Function deployment
From the Supabase CLI:
```bash
supabase functions deploy create-employee-account
supabase secrets set SUPABASE_SERVICE_ROLE_KEY=YOUR_SERVICE_ROLE_KEY
```

The Edge Function automatically receives SUPABASE_URL and SUPABASE_ANON_KEY in Supabase's environment. Never put the SERVICE_ROLE key in GitHub or `config.js`.

## Suggested account creation
Use each employee's official/work email address if available.

Example:
Employee: IRENE BARBERO-RACHO
Code: CSWDO-01
Email: [official email]
Temporary password: [admin-generated password]

After giving the credentials to the employee, they can log in on their phone.

## Security
- Do not share the service-role key.
- Use HTTPS/GitHub Pages.
- Require employees to change their temporary password after first login if your authentication flow supports it.
- Consider enabling MFA later for the Admin account.
