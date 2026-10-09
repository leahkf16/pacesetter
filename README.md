# pacesetter
A personalized fitness preparation app featuring workout plans, performance tracking, hydration goals, and athlete-coach dashboards.

## Quick start

1. Upload all files in this folder to a public GitHub repository.
2. Repository Settings → Pages → Deploy from branch → main / root.
3. Open the resulting HTTPS link on a phone. iPhone Safari → Share → Add to Home Screen; Android Chrome → Add to Home Screen/Install.
4. Athlete: Settings → set test date, goal, and baseline. Scores → record new benchmark every 2–3 weeks.
5. Workouts change across a 3-week variation cycle and increase modestly with training week. Logged 2-mile scores adjust suggested paces; reported high fatigue and the final seven days reduce volume.

## Coach dashboard on a separate phone

**Cloud setup is required; no hosted backend is included in this ZIP.**

1. Create a Supabase project at https://supabase.com and enable Email authentication.
2. In Supabase SQL Editor, run `supabase_setup.sql`.
3. Both athlete and coach enter the SAME project URL and **public/anon key** in Settings. NEVER enter a service-role key.
4. Each signs up using a DIFFERENT email/password, confirms email if prompted, then signs in.
5. Athlete: sign in, press Sync now, then Generate coach invite code. Send code privately to coach.
6. Coach: switch to Coach mode, sign in to their own account, enter invitation code and press Link athlete.
7. Coach uses Sync now to refresh from athlete. This is manual sync, not live push updates. Athlete should also sync after sessions when online.

**Security limitations:** Coach invite codes are bearer secrets and allow any signed-in user holding a code to read the athlete's profile. To revoke a code, delete it from `coach_invites` in Supabase. This starter does not include invitation expiration, per-coach authorization, account recovery UI, or production-grade security review. The coach's note is local to the coach device in this starter and is not delivered to the athlete. The athlete's cloud data is private to their own account except through the invite-code function. Local browser storage is not encrypted.

## Notes

- Suggested running paces are estimates, not clinical prescriptions. Check the athlete's actual fitness and tolerance.
- Verify official PT test scoring, form, rest periods and eligibility rules. Targets currently: 63 push-ups, 56 sit-ups, 18:00 2-mile, or 70 PACER shuttles.
- The athlete has passed before; this app uses an editable intermediate-style starting baseline. Replace all sample values with actual results.
- Exercise demonstrations are text-based instructions, not video demonstrations.
- A CSV export is available on the Scores tab.
- The app works locally without a database; cross-phone sync requires Supabase and connectivity.

## Recurring PT tests and birthday
The athlete's birthday is prefilled as December 4, 1999. The app shows a personal birthday greeting on December 4 whenever it is opened. Age brackets can automatically update based on the scheduled PT test date. The next test date is intentionally left blank because 'about three weeks' is not an exact date; set it in Settings. After each PT test, archive the date and latest recorded results, then enter the next test date. Archived tests are preserved locally and in the existing athlete sync payload if configured. Birthday messages are in-app, not push notifications; the app must be opened to display them.


## Hydration Station
The athlete has a Water tab, quick-add drink sizes, custom entry, daily total, editable daily tracking target, undo, and seven-day history. The coach dashboard shows the athlete's latest logged hydration after cloud synchronization. The default 2,500 mL is a **placeholder**, not a USAF prescription or a medical recommendation. Heat, duration, sweat rate, diet, and medical conditions change fluid needs. Avoid forced overdrinking and follow medical/unit heat guidance.