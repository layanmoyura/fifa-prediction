# FIFA Prediction

A lightweight, browser-based World Cup prediction tracker for managing upcoming matches, recording predictions, and calculating leaderboard scores.

This project is built as a single-page HTML application and stores its data in JSONBin. It supports Netlify Identity for login/signup and allows admins to create matches, finalize results, and adjust odds multipliers.

## Features

- Create and track upcoming FIFA matches
- Allow users to submit predictions for each fixture
- Support paired predictions via a `Pair Order` field
- Calculate team standings and leaderboard scores
- Finalize match winners and mark completed games
- Update odds multipliers for a match
- Restrict administrative actions to admin users
- Use Netlify Identity for authentication
- Store all match and user data in JSONBin

## How it works

- Users sign in through the Netlify Identity widget.
- Admins can add matches, assign a final winner, and update odds.
- Any logged-in user can submit predictions for a match.
- The leaderboard is recalculated based on the current match outcomes and multipliers.
- Paired predictions are treated specially and can affect scoring differently from unpaired predictions.

## Project structure

- `index.html` — main front-end app and logic
- `README.md` — project documentation

## Tech stack

- HTML
- CSS
- JavaScript
- Netlify Identity
- JSONBin API

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/layanmoyura/fifa-prediction.git
   cd fifa-prediction
   ```

2. Open `index.html` directly in a browser, or deploy it to a static host such as Netlify.

3. Configure the app with your JSONBin credentials and Netlify Identity environment setup:

   - Update the `BIN_ID` and `SECRET_KEY` values in `index.html`
   - Ensure Netlify Identity is enabled for your deployed site

## Usage

### For regular users

- Sign in with Netlify Identity
- Enter a predictor name and select a team for a match
- Save your prediction
- View the live leaderboard and match statuses

### For admins

Admins can:

- add new matches
- finalize match winners
- update odds multipliers
- manage who can participate (if configured in the stored database)

The admin role is granted automatically for emails containing `layan` or `yasiru`, or for accounts explicitly marked as admin in the stored user database.

## Data storage

The app stores all match, prediction, and user state data in a JSONBin record. The app expects a structure similar to:

```json
{
  "users": {
    "user@example.com": {
      "role": "admin",
      "is_enabled": true
    }
  },
  "matches": [
    {
      "id": 123456789,
      "date": "2026-06-15",
      "team1": "Argentina",
      "team2": "Brazil",
      "odds": 2,
      "winner": "Argentina",
      "bets": [
        {
          "bettor_name": "Player 1",
          "picked_side": "Argentina",
          "pair_order": "1"
        }
      ]
    }
  ]
}
```

## Deployment

This app is designed to be deployed as a static website. A simple Netlify deployment works well because it supports the Netlify Identity widget used by the app.

## Notes

- This is a lightweight front-end app intended for personal or small-group prediction leagues.
- The repository currently contains a static HTML implementation and does not include a backend service.
- For production use, you may want to add validation, stronger admin controls, and backup strategies.

## License

This project is provided as-is for personal or internal use. If you plan to publish it publicly, add an appropriate license file according to your preferred terms.

