# CSWDO Employee QR Logbook — Online Supabase + GitHub Pages

## Files
- index.html — employee/admin web app
- config.example.js — copy to config.js and add Supabase URL + anon key
- supabase_schema.sql — create database, policies, RPC, and 35 employees
- office-qr.html — printable official office QR
- DTR_TEMPLATE.xlsx — original DTR template supplied by the office

## Setup
1. Create a Supabase project.
2. Open Supabase SQL Editor.
3. Run all of `supabase_schema.sql`.
4. In Supabase Authentication, create employee accounts and one admin account.
5. For each employee account, insert/update `public.profiles` so the auth user's UUID is linked to the correct employee.
6. Copy `config.example.js` to `config.js` and enter the Supabase Project URL and anon/public key.
7. Upload the files to a GitHub repository.
8. Enable GitHub Pages for the repository.
9. Open the generated HTTPS URL on employee phones.
10. Print `office-qr.html` and display the QR at the CSWDO office.

## DTR rules
5:00 AM–11:59 AM -> A.M. Arrival
12:00 NN -> A.M. Departure + P.M. Arrival
5:00 PM onward -> P.M. Departure
Undertime -> blank; no calculation

## Security
Do NOT put the Supabase service_role key in the website.
Only the anon/public key belongs in config.js.
Use strong passwords for accounts.
The secure `record_qr_attendance()` RPC determines the employee from the authenticated account and validates the office QR.

## Important
The generated DTR follows the structure of the supplied DTR template. For exact pixel/print reproduction of every merged cell, spacing, signatures, and footer in the XLSX, the final DTR renderer can be adjusted after the exact office-approved print layout is confirmed.
