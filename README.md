# NHS Healthcare Assistant visa sponsorship job alert

This project runs a scheduled GitHub Actions job that searches NHS Jobs for Healthcare Assistant and closely related clinical support-worker roles with positive visa sponsorship wording, then emails the result to `kennethoseinimako@gmail.com`.

## What it checks

- Healthcare Assistant, HCA, Healthcare Support Worker, Clinical Support Worker, Nursing Assistant, Maternity Support Worker, Patient Support Worker, and related NHS Jobs titles.
- Positive sponsorship wording such as Skilled Worker sponsorship, Health and Care Worker visa, visa sponsorship eligibility, or Certificate of Sponsorship.
- Excludes listings that say sponsorship is unavailable, not eligible, cannot be offered, or require existing right to work.

## GitHub setup

1. Create a private GitHub repository.
2. Add these files to the repository.
3. In GitHub, open the repository settings.
4. Go to **Secrets and variables** -> **Actions** -> **New repository secret**.
5. Add the SMTP secrets below.
6. Open the **Actions** tab and enable workflows if GitHub asks.

## Required secrets

Use the same values from your existing SMTP setup:

- `SMTP_HOST`
- `SMTP_PORT`
- `SMTP_USERNAME`
- `SMTP_PASSWORD`

Recommended optional secrets:

- `EMAIL_FROM`
- `EMAIL_REPLY_TO`
- `SMTP_USE_SSL`
- `SMTP_USE_STARTTLS`

For the SMTP mode that worked in the earlier NHS IT workflow, use:

- `SMTP_HOST` = `loopsol.com`
- `SMTP_PORT` = `465`
- `SMTP_USE_SSL` = `true`
- `SMTP_USE_STARTTLS` = `false`

## Schedule

The workflow runs every day at 08:30 UTC, which is 09:30 in London during British Summer Time. You can also run it manually from GitHub:

**Actions** -> **NHS Healthcare Assistant job alert** -> **Run workflow**

## Local test

To test without sending:

```bash
python scripts/nhs_healthcare_assistant_email_alert.py --dry-run
```

To send locally, set the same SMTP environment variables and run:

```bash
python scripts/nhs_healthcare_assistant_email_alert.py
```
