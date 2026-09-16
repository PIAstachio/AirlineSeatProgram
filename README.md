# ✈️ Airline Seat Reservation System

![C++](https://img.shields.io/badge/C%2B%2B-00599C?logo=cplusplus&logoColor=white)

An interactive command-line booking system that manages a 25-seat cabin, handling
bookings, cancellations, and seat changes while preventing double-booking.

**Skills shown:** C++ · state management · modular function design · input handling

## What it does
| Option | Action |
|---|---|
| 1 | Show the full seat map with booked/open status |
| 2 | Count available seats |
| 3 | List only open seats |
| 4 | Book a seat (rejects seats already taken) |
| 5 | Cancel a booking |
| 6 | Move a booking to a different seat |

## Design decisions
- **Separated data from display.** Seat labels and booking status live in two parallel
  vectors, so the seat layout can change (more rows, different letters) without
  touching the booking logic.
- **One function per operation.** Each menu action is an independent function, which
  keeps `main()` short and makes each operation testable on its own.
- **Deliberate use of references.** Functions that only read the seat map take it by
  `const` reference, and only functions that modify bookings get write access. This
  avoids copying data and prevents accidental changes.

## Run it
```bash
g++ -o seats "Airline Seat Booking Program.cpp"
./seats
```

## What I'd improve next
- Validate seat labels so invalid input like `9Z` gets a clear error message
- Make seat changes atomic, confirming the new seat is open before releasing the old one
- Replace the parallel vectors with a `struct` or `map` to tie each label to its status
