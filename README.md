# Pre-req Vault with registration CPI

Turbin3 Q4 2026 Builders Cohort prerequisite.

## What I changed
Extended the `withdraw` instruction with a CPI to Turbin3's registration
program (`initialize`), passing my GitHub username. Uses `CpiContext::new`
(not `new_with_signer`): my wallet's signature carries into the CPI, and the
application account is the registration program's PDA, not mine.

## Deployment (devnet)
- Program ID: `CPjBmh3FFCy5bDzrm8kbXCcuFgDofJ2cgqLXXho7EYjp`
- Withdraw + registration tx: `3i1koDZgrk7rzoDNgKTLxDi2gUHTTR7g33ot41SBktn9WjNUutUT4iSpoL6CJeCFeeSm6NTfm4HSNLqu8qvQ39ss`
  (logs show the registration program at invoke depth 2, called by my program)

## Notes
- `constants.rs` and `error.rs` are unused leftovers from a counter template.
- The Rust test (LiteSVM, a local simulated chain) is commented out, because the
  registration program only exists on devnet. The TypeScript test runs on devnet.