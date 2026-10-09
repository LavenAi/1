# Laven AI — Project Blueprint

Status: Planning blueprint. Owner-confirmed requirements and selections made under explicit owner delegation are recorded separately from proposed implementation defaults. Model/runtime feasibility still requires validation; no app has been built or deployed through this planning work.
Language: English.
Working roles: This assistant is the project Director, confirmed by the owner. The Director defines scope, priorities, budgets, executor briefs, and acceptance reviews. Application implementation belongs to a separately assigned Executor; preparing planning documents does not assign or launch an Executor.
Discovery questions: Thai, as requested by the owner. Ask ten questions per batch from Steps 163–172 onward, confirmed by the owner; there is no fixed total-question cap. Record batch answers before presenting the next batch.
Product name: Laven AI, confirmed by the owner in Step 98.
Desired domain: lavenai.space. Not yet purchased; availability, registration price, and renewal price are unverified.

## 1. Project Goal

Build Laven AI as an actual startup product: an online conversational AI companion with real user accounts, cloud-persisted data, and live AI/voice integration. The owner has reconfirmed an online production web app accessed through mobile and desktop browsers. Retain Next.js/TypeScript, Supabase, Cloudflare, and the cascaded OpenRouter architecture. A local prototype or simulated browser demo is a development aid, not the final product or launch deliverable. The web app remains the base platform; R001 records the first-release floating-companion requirement; Windows is the selected floating OS; exact supported Windows versions and runtime remain pending.
Position the product as a Hyper-Personalization App, with an AI companion as its primary use case. Personalization is a core product capability.
Define the product step by step with the owner before implementation.

### Current Avatar Revision R001 - October 9, 2026

The owner's latest clarification takes precedence over historical circle-only/gallery-only appearance and blanket floating-client deferral. See [avatar-plan.md](avatar-plan.md) for the detailed contract.

- First release: a simple minimalist lavender ball is the default living companion; users may replace it with their own purchased, already rigged 2D anime model.
- First-release local import is confirmed. The earlier suggestion to defer every rigged model is superseded; purchasing/commissioning an official Laven anime character is optional future work.
- Imported model files remain locally on the importing user's computer/device. No cloud upload, model-file synchronization, repository copy, or provider submission. Account settings/history/memory otherwise retain their existing sync.
- The latest clarified type is rigged 2D. A 3D importer, automatic rigging, and arbitrary-format support are not selected.
- Format is not selected. Live2D Cubism is the Director's first candidate for evaluation, subject to owner selection, SDK release terms, compatible packages, and real-device evidence.
- Proposed device-local appearance controls in Settings > My Companion: Import, Preview, Use model, Replace, Remove local model, and Use default ball. Keep existing gallery choices and other companion settings. Model selection/references should be local and account-partitioned; another device requires a separate import and uses a valid gallery/ball fallback.
- Browser-local persistence is not a guaranteed backup: test quota/eviction/private browsing and explain re-import after clearing site data. Exact package/resource limits and model animation mappings remain engineering proposals to validate.
- The owner confirmed floating above other applications in the first release on October 9, 2026. Windows is selected as the first floating OS; Android floating and other desktop OS clients are later; web-only delivery does not pass this release gate. T078-T082 cover the platform decision and companion-client work. An in-page widget does not prove cross-app overlay support.
- T070-T077 cover avatar/import delivery. No renderer, import, runtime installation, purchase, native client, or real-device check has been completed. Existing voice, captions, privacy, cancellation, and usage rules remain in force.

### Confirmed Product Priorities

1. AI companion: the primary product focus, centered on everyday conversation and companionship.
2. General assistant: the next priority, supporting everyday questions and tasks.
3. Language tutor: a later expansion, supporting speaking practice and language learning.

These priorities guide a real startup product. The initial online release remains a private trial for the owner and permitted invitees, followed by a later wider release when readiness is demonstrated. The wider audience, public-registration timing, and commercial pricing remain to be defined; startup intent does not automatically select a public paid launch.

### Confirmed Initial Release Scope

- Start with real online use by the owner and permitted invitees, rather than accepting a local-only demo as the release.
- Prioritize a working end-to-end conversation experience that the owner can evaluate and refine.
- The initial release is an invite-only trial for the owner and explicitly permitted invitees. Open public registration is outside this release's selected scope.
- Google and email/password authentication, Supabase, and Cloudflare hosting have been selected. Use an allowed-email list for private-trial access, managed through an owner-only section in the application's Settings.

### Confirmed Device Priorities

- Support mobile and desktop equally through a responsive web interface.
- Give the core conversation experience and its essential controls equal functional priority on both device types.
- Adapt page layout and navigation to screen size. Exact breakpoints, navigation patterns, and supported browsers remain to be defined.

### Confirmed Account and Cross-Device Data

- Use one account across mobile and desktop.
- Synchronize the companion profile, personalization and appearance settings, conversation history, and personalization memory across devices signed into that account.
- Support both Google sign-in and email/password sign-in in the first release.
- Use Supabase Auth for account identity and Supabase Postgres for shared persistence. Authentication flows and access policies remain to be specified.
- Limit application access to the owner and invited accounts. Authentication alone does not grant access to the private trial; enforce invitation eligibility on protected pages and server API requests.
- The owner permits an invitee by adding their email address to an allowed-email list stored in Supabase. An authenticated user must have a verified email matching an active entry to access the trial. Apply the same access rule to Google sign-in and email/password sign-in, using server-validated identity rather than an email submitted by the browser.
- Adding an email grants trial eligibility; the invitee still signs in or completes the permitted account-registration flow. Trial invitation links and invitation codes are outside the selected initial mechanism. Only the owner may manage allowed entries through Settings > Trial Access. Owner-role setup remains to be specified.
- Each invited user has an independent companion profile, settings, history, summaries, and personalization memory. Cross-device synchronization applies within that user's account and does not share personal data with other invitees.
- Revoking trial access blocks application access but preserves the account's companion, settings, history, summaries, fact/preference memories, and deletion exclusions. Revocation is an eligibility change, not account or data deletion. Reinstating the same account restores access to its retained data.
- Reject subsequent protected requests for a revoked account, even if its authentication session remains valid. Enforce this in application endpoints and database access policies; background AI jobs must also check current eligibility.
- Revocation immediately stops the affected account's active conversations on every signed-in surface, confirmed in Step 142. Stop microphone capture, speech playback, captions, proactive follow-ups, and unfinished reply generation; discard transient audio buffers and close active voice-session accounting without resetting recorded usage. Do not allow an already accepted reply to finish. Preserve text already saved before revocation, while blocking late response appends and new memory writes after eligibility is removed. Request upstream cancellation where supported and reject obsolete results even when provider cancellation is unavailable. Access-state propagation, cancellation, and metering need validation; immediate stopping is the intended behavior, not a zero-network-delay guarantee. Reinstatement must not automatically restart the microphone or cancelled replies; require an explicit session start or Resume and normal eligibility/usage checks.
- Account linking between the two sign-in methods and account recovery flows remain to be specified.
- Allow simultaneous voice sessions for the same account across devices and browser tabs. Starting another session does not transfer or stop an existing one. All sessions share the account's companion, settings, memory, and daily allowance, subject to the selected account synchronization rules.
- Simultaneous sessions for the same account use one shared active conversation. Combine their user and AI messages into the same ordered conversation history and synchronize it across the account's open surfaces. AI replies use the shared conversation context rather than isolated session transcripts. This does not share a conversation across different user accounts.
- When a new voice session starts after all previous sessions have ended, create a new conversation by default instead of automatically resuming the previous one. Retain the saved companion settings and eligible personalization memory; start with a fresh message thread. The user may explicitly resume an unexpired conversation through History.
- Joining an already active shared conversation or explicitly resuming a paused session does not create a fresh thread merely because a surface opens. Coordinate simultaneous new-session starts so they join one new shared conversation rather than creating competing threads.
- Explicitly starting another conversation or resuming a different unexpired history thread switches every active session for the account to that same conversation. Synchronize the selected conversation and its message context across surfaces without creating independent active threads. Keep session-time accounting continuous through the switch, and preserve the previous conversation's history until its normal expiry or deletion.
- End obsolete playback and captions from the previous conversation on affected active surfaces, and prevent late responses or recordings associated with the old conversation from being attached to the newly selected thread. Switching does not change reply-audio routing: each new reply still plays only on its originating surface. Atomic switching, in-flight turn cancellation, and coordination with old-conversation summary jobs require implementation validation.
- Offline behavior, exact synchronization timing/transport, and concurrent data-edit conflict resolution remain to be specified. Keep each turn associated with its originating session and conversation so audio delivery and interruptions can be handled consistently.

### Self-Service Account Deletion

- Provide a Delete account action in Settings for users to request deletion of their own app account and personal app data. Require explicit confirmation that identifies the affected account and explains the data scope. After confirmation, mark the account as pending deletion for seven days before beginning permanent cleanup.
- Record a server-controlled deletion deadline seven elapsed days after the confirmed request, and display it with a Cancel deletion action. Cancellation before that deadline removes the pending request; it does not reset usage, restore separately expired/deleted history, or override trial-access revocation. Signing in alone does not cancel the request.
- During the seven-day pending-deletion period, restrict the account to its deletion-status page, deadline, Cancel deletion action, and sign-out. Block normal Conversation, History, Settings, and admin access, stop all of the account's active voice sessions, and pause its AI conversation and memory-learning jobs. Preserve data pending permanent cleanup, subject to independent history expiry. Do not change the user's saved memory preference merely to enforce the pending state.
- Cancellation returns the account to its normal eligibility and usage checks; it does not automatically restart microphone listening. Continue to prevent pending or late AI work from writing personal content while deletion is pending, even if a previous session or queued job was created before the request.
- The personal-data scope includes the companion profile, saved settings, conversation messages, conversation summaries, fact/preference memories, deletion exclusions, and temporary audio-processing/playback buffers. Unlike history deletion or expiry, account deletion does not preserve personalization memory for later use.
- When permanent cleanup begins, block new conversation and memory work, stop the account's voice sessions, and prevent pending jobs or late provider responses from recreating deleted personal data. Invalidate its app sessions as part of completed deletion. Implement server-authorized deletion and cancellation for the caller's own account, rather than trusting a client-supplied account identifier. Recheck the current pending state and deadline before cleanup so a cancellation cannot race with a stale deletion job.
- The seven-day account-deletion waiting period is separate from seven-day conversation-history retention. Existing history expiry rules remain in effect; cancelling account deletion does not recover messages already removed by those rules.
- After permanent account deletion, the email's prior trial authorization must no longer grant access to a fresh account. Require the owner to authorize the email again through Settings > Trial Access before a new signup can access the trial. A newly authorized account starts with fresh personal data; do not restore the deleted account's history, memories, or settings. Cancelling a pending deletion does not itself require a new invitation, subject to existing access eligibility.
- Keep shared monthly spending already incurred in the aggregate budget total. Owner-account handling, backup/provider retention, and exact cleanup coordination remain to be defined; this is a product requirement, not verified end-to-end deletion behavior.

### Confirmed Main Screen Direction

- Use a voice-focused main conversation screen.
- Place a minimalist lavender ball at the center as the default living companion (R001).
- Animate actual local listening, thinking, and speaking states; a supported imported rigged 2D model can replace the ball in the first release.
- Let users customize the image shown within the circle by selecting a ready-made image from the app's gallery.
- Use the lavender ball as the default before a gallery or valid device-local model is selected.
- Preserve the static-image gallery. R001 additionally selects local import of a user-owned, already rigged 2D model; static portrait uploads and a 3D importer are not selected by that clarification.
- The initial gallery offers both flowers/nature/minimal abstract images and cute illustrated characters/animals, confirmed in Step 115. Keep the collection visually consistent with the minimal lavender interface. Exact assets, collection size, image presentation, and how the selected image interacts with state animations remain to be defined. The selected gallery image is part of the account-synchronized companion profile. No gallery assets have been created yet.
- Include a microphone control.
- Show captions below the central voice visualization, using the owner's "like Pingo" description as a reference for this placement. No other Pingo-specific appearance or behavior has been specified.
- Let the user open the conversation text when needed, showing messages from both the user and the AI.
- The conversation text view supports reading and sending typed messages through a text input and Send button.
- Open the full text conversation within the existing voice screen: a side panel on desktop and a bottom sheet on mobile.
- Both layouts support reading the conversation and sending typed messages.
- Every AI reply to a typed message is shown as text and spoken aloud on the surface that submitted the message, regardless of whether a voice session is active. Other signed-in surfaces receive the synchronized text without playing that reply's audio. This does not itself start microphone listening.
- Sending a typed message while a local AI reply is speaking interrupts that local speech and starts processing the new message without waiting for the old speech to finish. Typing a draft alone does not interrupt. Keep the new reply routed to the surface that submitted it, and do not stop other sessions merely because this surface sent a message.
- Speaking over the AI or sending a new message stops both local speech and unfinished generation of that reply, confirmed in Step 122. Clear obsolete local playback queues, transient audio buffers, and captions; stop requesting further speech for the cancelled reply. Preserve already saved shared text. Mark that reply as interrupted in the data model rather than treating it as a completed response. Reject late text/audio from the cancelled generation so it cannot append to history or restart playback. Request upstream cancellation where supported; exact provider cancellation and interrupted-reply presentation require validation. Begin capturing the new spoken turn immediately, then apply the normal two-second utterance-end wait, or process a sent text message directly. Independent turns/sessions are not cancelled by this local interruption.
- If speech generation or playback fails after reply text is available, show the reply text with a localized "Retry audio" action. Preserve the normal text-plus-speech intent, but allow the available text to be read without waiting for audio recovery. This failure exception does not bypass daily-allowance or monthly-budget exhaustion rules.
- Captions beneath the visualization show only the AI's response while the AI is speaking.
- Add a Show AI captions toggle in Settings, enabled for new accounts, confirmed in Step 167. Synchronize the saved preference across the account. Hiding captions does not mute AI speech, cancel generation, or remove conversation text from the chat panel. The existing word-by-word, wrapping, and sentence-clearing behavior applies whenever captions are shown.
- Start AI captions beneath the circle on one row. Reveal whole words progressively as they are spoken and wrap onto additional rows when the available width is filled. Keep accumulating the same sentence until its spoken completion; do not horizontally scroll it or replace earlier words with a shorter segment while that sentence is still being spoken.
- When the sentence finishes being spoken, clear all rows of the completed sentence before revealing words for the next sentence. Clear the final sentence when its speech ends; the full reply remains available in the chat panel. Captions follow local playback only and stop/clear on an interruption or failed playback, so obsolete words do not continue appearing.
- Responsive spacing for unusually long sentences, the clear/transition animation, and precise word-to-audio alignment remain implementation details to design or validate. No fixed row limit has been selected. Keep captions readable without covering session controls. Word segmentation must handle Thai and mixed Thai-English without assuming that every word is separated by a space.
- The full conversation text view includes both speakers, while the captions beneath the circle show only the AI's speech.
- Prototype-only exception under delegated Step 182: if accurate word alignment is not ready, the first prototype may show the currently spoken sentence and clear it at actual speech completion. Identify this temporary behavior during prototype review; the final feature remains accurate progressive word reveal with wrapping and sentence clearing.
- If transcription is incorrect, the user sends a correction as an ordinary new typed message, confirmed in Step 125. Do not add transcript-editing or answer-regeneration controls for the first release. Preserve the original transcript and reply as history, then process the correction through the normal typed-message pipeline, including interruption, text-and-speech delivery, synchronization, and usage checks. Later memory processing must consider eligible corrections in context rather than treating a corrected transcription as an unqualified fact.

### Confirmed Visual Theme

- Use a minimalist visual style with lavender purple as the default primary accent color.
- Support light and dark themes.
- Allow users to select light mode, dark mode, or follow the device/system theme.
- Allow users to change the primary accent color; lavender is the default.
- Exact color values, typography, spacing, and animation treatment remain to be defined.

### Confirmed Interface Languages

- Support Thai and English for menus, buttons, and settings.
- Initialize the interface language from the device language.
- Let users switch the interface language in Settings and synchronize their saved choice across devices.
- If the device language is neither Thai nor English and no interface preference has been saved, use English, confirmed in Step 147. Match Thai and English device locales to their supported interface language, including regional variants. A saved interface-language choice takes precedence over device detection across sign-ins and devices. Users may change it in Settings; conversation-language detection remains independent of the interface language.

### Confirmed Companion Direction

- The first release has one main AI companion.
- New accounts start with the companion name Laven, confirmed in Step 146. Keep this default spelling in both Thai and English interfaces. Users can change the companion's name, personality, and selected gallery image at any time in Settings > My Companion. Do not overwrite a saved custom name when changing interface language, accepting onboarding recommendations, or signing in on another device.
- Multiple companion profiles and a companion-switching interface are outside the selected first-release scope.
- Users can choose the AI companion's personality instead of being limited to one fixed personality.
- A "Pingo-like persona" is a desired later expansion. Its reference and exact behavior have not yet been defined; do not assume it requires an avatar, animation, or a specific relationship style.
- The initial personality customization model combines selectable presets with adjustable personality traits.
- Users can start with a preset and refine individual traits to suit their preferences.
- Use a separate five-position slider for playfulness, gentleness, and response length, confirmed in Step 159. Use five discrete levels rather than a 0–100 percentage scale: Very low, Low, Medium, High, and Very high, localized as น้อยมาก, น้อย, ปานกลาง, มาก, and มากที่สุด. Represent levels consistently as 1–5 in the proposed implementation, with no intermediate values. Adapt visible wording for response length so the low end clearly means shorter replies and the high end means more detail; exact localized length labels and per-level guidance remain to be defined. These controls express style preferences, not measured percentages or guarantees of AI behavior. Step 160 selects initial values of Medium playfulness, High gentleness, and Short replies for new accounts. Custom-instruction precedence, contextual adaptation, autosave, and preserving saved traits when changing presets still apply. No additional trait is selected.
- The initial response-length preference for new accounts is short and concise, roughly one to three sentences, confirmed in Step 112. This is a style target rather than a hard limit; the confirmed context-adaptation policy and user-adjustable response-length slider still apply. AI may provide more detail when the user requests it or the context needs it without rewriting the saved preference.
- Include an optional free-text field for additional personality/conversation-style instructions in Settings > My Companion, confirmed in Step 116. Users can write, edit, or clear it alongside the existing presets and trait sliders. Store it as an account-synchronized companion setting; new accounts start with an empty field, and first conversation does not require filling it in. It remains a personality setting when personalization memory is disabled. Limit it to 1,000 characters and show a character counter, confirmed in Step 172. Validate the limit on client and server; preserve over-limit or failed-save drafts for correction instead of silently truncating them or applying an invalid value. Unicode counting and validation details require implementation testing. Settings autosave follows Step 158.
- When saved free-text personality instructions conflict with a preset or trait slider, give the custom text precedence for that conflicting style preference, confirmed in Step 117. Presets and sliders continue guiding preferences not addressed by the custom text. Keep all saved values unchanged unless the user edits them. Existing context adaptation still applies without rewriting settings. Personality instructions do not change server-enforced access, memory eligibility, search permissions, or usage limits.
- Automatically save edits in Settings > My Companion without a Save button, confirmed in Step 158. This covers the name, preset, traits, custom instructions, gallery image, selected voice, and speed. Show saving, saved, and failure states; if a save fails, preserve the local draft for retry and keep the last successfully saved settings effective for AI replies. Coalesce rapid typing/slider edits instead of writing on every input event; exact timing and concurrent-edit handling require validation. Save only changed fields so unrelated settings are not overwritten. Previewing a voice does not save its selection, and merely displaying onboarding recommendations does not accept them. Keep onboarding's explicit Continue/Skip and recommendation-acceptance flow separate. Existing next-reply personality and voice/speed rules apply to successfully saved values; changing settings does not itself call AI or replay speech.

### Confirmed Initial Personality Presets

- Warm and gentle: caring language and a reassuring conversational tone.
- Playful and talkative: light humor and an energetic conversational tone.
- Calm and attentive: patient listening and a composed conversational tone.
- Friendly and direct: approachable language and clear, concise responses.
- All four presets are confirmed for the first release. Users can select a preset and then adjust the selected personality traits in Settings > My Companion.
- New accounts start with Warm and gentle. Initial traits are Medium playfulness (3/5), High gentleness (4/5), and Short replies (2/5), confirmed in Step 160. Short replies target roughly one to three sentences, with the existing context-adaptation policy. Users can begin their first conversation without choosing a personality preset first and can change it later in Settings > My Companion. Initialize these values only for new accounts; existing accounts retain their saved selection and traits. Switching presets still preserves saved trait values.
- After the first eligible successful sign-in, offer optional onboarding with the AI interview first, followed by optional personality, gallery image, and voice customization, confirmed in Step 140. Conduct the interview using saved/default companion settings. After customization, Continue saves chosen settings and opens a new normal Conversation; skipping customization retains saved/default settings. Keep a way to skip onboarding and begin with defaults without mandatory preset selection. Later customization remains in Settings > My Companion. Proposed implementation: synchronize completed/skipped stages at account level so another device does not repeat setup. Do not activate the microphone merely because setup opens; interview capture requires explicit Start interview, while normal Conversation entry follows its saved start preference and permission checks. Existing access and pending-deletion restrictions take precedence over setup routing.
- After the interview, recommend a personality preset, gallery image, and voice based on the user's answers. Offer only choices from the actual available preset, image, and voice catalogs. The user may accept suggestions or choose alternatives individually; apply only the fields they explicitly accept and save. Preserve saved trait sliders when changing presets, and do not implicitly change the companion name, speaking speed, or custom instructions. Existing custom-instruction precedence remains in effect.
- Generate onboarding suggestions from the current interview context or a transient onboarding draft. When memory is disabled, do not retrieve disabled saved memory or create a hidden personalization profile; explicit acceptance may still save ordinary companion settings. Recommendation generation must respect eligibility and AI-budget controls. Whether suggestions can share an existing interview-completion call, their cost, and handling unavailable catalog entries require implementation validation.
- Include an optional AI-led onboarding interview at first eligible sign-in, replacing the form-style quiz in Step 129. Gather information such as nickname, interests, and preferred conversation style, alongside the companion setup selected in Step 126. The AI asks one friendly question at a time and adapts the next question to the user's answers, without treating the exchange as a scored knowledge test. Keep a Skip action so users can begin with defaults and introduce themselves later through conversation or Settings > Memory. Do not repeat it on every sign-in. Exact prompts, sequence, presentation, and completion/editing controls remain to be defined.
- On completed onboarding, save eligible introductory facts/preferences automatically as manageable memory items, confirmed in Step 134. Do not require a separate review-and-confirm screen for ordinary eligible saving while memory is enabled. Users can view, edit, and delete the resulting items in Settings > Memory. Companion configuration stays in its account-level settings. Keep memory disabled when the user has disabled it, and do not automatically learn from answers recorded during that interval. The existing explicit Enable memory and save this action remains available for an explicit remember request, with item-specific confirmation and no unrelated backfill. A new interview answer alone does not restore a previously deleted fact. Skipped or unfinished interview content does not trigger automatic onboarding-memory saving.
- Keep the core companion-introduction interview short, approximately three to five questions, preserving the length selected in Step 128. Clarifying follow-up questions count toward that range so adaptive questioning does not create an indefinite interview. Include the three requested language-learning questions as an optional additional onboarding branch now, confirmed in Step 133. If all core and learning questions are asked, the total is approximately six to eight. Skip redundant questions and allow skipping the learning branch. Let subsequent eligible conversations and direct memory entry expand personalization over time. Exact prompts and the final flow remain to be defined.
- Use the existing standard OpenRouter LLM route to conduct the interview, with the configured companion personality and concise response style. Apply normal account access, daily allowance, monthly budget, cancellation, and memory rules. AI-generated interview turns consume the shared inference budget. If AI calls are unavailable, allow skipping the interview and completing companion setup without bypassing limits. Retained interview content follows the existing text-history policy; generated audio is not stored for reuse. The interview has its own conversation record, separate from the normal conversation started after completion, confirmed in Step 135. Exact transcript presentation remains to be defined.
- Deliver the onboarding interview through voice as the primary channel, with readable question/answer text and typed-answer fallback, confirmed in Step 130. Use the selected OpenRouter STT/LLM/TTS pipeline and default continuous-voice behavior, including the approximately two-second utterance-end wait, incremental AI speech, and normal interruption rules. Require an explicit Start interview action and microphone permission before voice capture, rather than silently starting on setup entry. Apply the shared daily allowance and monthly AI budget; active interview time counts as voice-session time without double-counting its playback. Typed responses remain available when speech input is inconvenient or unavailable, with ordinary text-and-speech reply behavior and the existing out-of-session playback rule when no voice session is active. Preserve Thai/English handling and no audio storage for reuse. Validate the actual route and device behavior.
- Use Variant 1, Start with enjoyable things, as the friendly onboarding approach, confirmed in Step 132. Also cover the owner's requested core information: preferred name/nickname, interests/hobbies, expectations of the AI companion, and preferred conversation style. Questions about current passions and an enjoyable free day can reveal interests naturally; the kind of friend the user enjoys can reveal role and style preferences. Treat these as adaptive coverage goals rather than requiring every example question verbatim. If an answer covers another topic, avoid redundant questioning. Keep optional/skippable participation. Step 133 adds the language-learning questions during onboarding, as described below.
- Proposed implementation for Step 134: an interview-completion job extracts and saves eligible facts once, using the existing LLM route, access/usage controls, account isolation, and duplicate/conflict handling. Keep interview content pending for personalization until completion so an inactivity summary job cannot bypass this boundary. This completion trigger serves onboarding facts; ordinary conversation summaries retain their end/inactivity schedule. Use the existing durable pending-job policy if inference is unavailable, recheck source eligibility and deletion/expiry rules, and do not claim memory was saved before successful persistence. Normal conversation learning after onboarding retains its previously selected behavior and silent-update preference.
- End the interview and its voice-session accounting when the interview completes. Step 140 then shows optional companion customization; once that stage is completed or skipped, enter a new normal conversation as selected in Step 135. Keep the interview transcript as a separate text-only History entry under the same seven-day retention rules. Apply the saved start preference, permissions, access/usage checks, shared-conversation switching, and new-conversation greeting rules on Conversation entry. Do not reset accumulated daily usage or the monthly budget. Use only successfully saved eligible memory for personalization in the new thread; background onboarding-memory processing may still be pending. Mark setup completion once per account and deduplicate the transition so concurrent surfaces cannot create multiple normal threads or duplicate greetings. Closing during post-interview customization does not make the already completed interview unfinished; stage recovery must preserve that completion.
- If the app closes before the interview completes, begin a new interview on the next visit rather than resuming its prior answers/progress, confirmed in Step 136. Require the usual explicit Start interview action and checks before new voice capture. Preserve saved companion settings, existing memories, and accumulated usage; keep Skip available. Mark the old unfinished interview as abandoned for onboarding processing so delayed jobs cannot save facts from it or attach late output to the new interview. Its already accepted text remains a separate History entry until ordinary seven-day expiry; unsubmitted audio is not retained. This restart rule applies after closure and does not replace the existing explicit-Resume behavior for a temporary network interruption while the app remains open.
- When a user switches personality presets, preserve the current saved trait slider values. Change the preset's conversational style without resetting playfulness, gentleness, response length, or other saved trait adjustments. Apply both the selected preset and the retained trait values as the personality baseline; context adaptation still does not rewrite saved settings.
- Saving a personality preset, trait values, or custom personality instructions takes effect for the next reply whose generation has not yet begun, confirmed in Step 156. Use the latest successfully saved account settings when reply generation starts, including greeting, interview, and proactive replies. Keep the already-started reply's personality baseline consistent through its text generation and sentence-by-sentence expressive speech; do not interrupt, regenerate, or rewrite that reply solely for a personality edit. A new conversation is not required. Synchronize saved settings across devices and validate update/generation ordering. This per-reply personality baseline does not freeze access, memory eligibility, search permissions, or usage checks, and does not add stored audio/style snapshots for replay. Voice/speed changes during speech follow Step 157.
- Offer Reset personality in Settings > My Companion, confirmed in Step 170. An explicit reset restores Warm and gentle, Medium playfulness (3/5), High gentleness (4/5), and Short replies (2/5), and clears custom personality instructions. Preserve name, image, voice, speed, history, and memory. This explicit action is an exception to ordinary preset switching, which preserves saved traits. Save the reset as one consistent operation, apply existing next-reply timing, and show save failures without falsely claiming success. Require confirmation under Step 174, explaining the restored traits and cleared custom instructions.

### Selected Onboarding Interview Direction and Alternative References

Variant 1 is selected, supplemented with the core information and language-learning questions requested in Step 132. Variants 2 and 3 remain unselected reference alternatives. Use the confirmed voice-first, one-question-at-a-time interview with readable text, typed-answer fallback, and Skip. Example wording is a starting point for localized Thai/English prompts; the AI can adapt it to answers. Participation in each topic is optional. The interview direction does not automatically change saved companion personality settings.

**Selected Variant 1 - Start with enjoyable things**

Purpose: get acquainted through light conversation and everyday interests.

1. What would you like me to call you?
2. What have you been especially into lately?
3. What does a free day you enjoy look like?
4. What kind of friend do you find fun to talk with?

Coverage requirements: learn the user's preferred name, interests/hobbies, what they want from the companion (casual conversation, listening, or help thinking things through), and their preferred conversational tone (gentle, humorous, or direct). Adapt follow-up wording to fill important gaps within the core interview's short range rather than mechanically repeating information already volunteered.

**Optional language-learning onboarding branch - confirmed in Step 133**

The owner requested these three questions:

1. What language do you want to learn?
2. How much [Language] do you know?
3. What's your purpose for learning it?

Use the language named in the first answer in the second question. Record the target language, self-reported familiarity, and motivation as user-provided preferences/facts under the automatic completed-interview saving selected in Step 134 and existing memory controls. Self-reported familiarity is not an assessed proficiency score. Allow the user to skip or say they are not interested in learning a language. Language-tutor delivery remains a later product phase, and the first-release Thai/English interface and speech scope remain selected.

Ask these questions during initial onboarding as an optional branch, confirmed in Step 133. If the user has no target language or declines this topic, skip the remaining learning questions. Use already provided answers rather than asking them again. The core three-to-five-question introduction plus this three-question branch is approximately six to eight questions when all are asked. These collected interests support future personalization; language-tutor features remain in their later phase.

**Unselected reference Variant 2 - Start with comfort and connection**

Purpose: learn how the user likes to feel supported and what makes conversation comfortable.

1. What would you like me to call you?
2. On a tiring day, how would you like a friend to be there for you?
3. What helps you unwind or feel at ease?
4. Are there conversation styles or topics you would prefer me to avoid?

**Unselected reference Variant 3 - Start with everyday life**

Purpose: understand the user's routine, current aspirations, and preferred companion role.

1. What would you like me to call you?
2. When during your day do you usually feel like having someone to talk with?
3. Is there something you would like to accomplish lately?
4. Would you most like me to think things through with you, encourage you, or chat casually?

These are interview topics, not additional scheduled outreach, reminders, or coaching features. Explicitly saved information follows the existing manageable-memory rules.

### Hyper-Personalization Scope

- Explicit customization through personality presets, individual trait settings, and an optional free-text personality field is confirmed.
- The AI learns automatically from conversations to adapt to the user's interests and conversation style.
- Users can explicitly instruct the AI to remember a preference, such as "Remember that I prefer short answers."
- Users can view, edit, delete, or disable memory.
- Include an Add memory action in Settings > Memory, confirmed in Step 118. Users can enter a fact/preference directly and deliberately save it alongside items created by eligible automatic learning or conversational remember requests. Scope it to the signed-in account and synchronize it across devices. Treat this as an explicit user-initiated remember action, without creating a conversation message or learning from unrelated history.
- If the user attempts to add a memory while memory is disabled, present the entered item with the existing Enable memory and save this confirmation. Without confirmation, keep memory disabled and do not persist the new item. A deliberate save can restore that explicitly entered previously deleted fact, lifting only its corresponding exclusion; automatic relearning of deleted facts remains prohibited. Directly added items remain editable/deletable and follow the existing automatic conflict-update policy rather than becoming permanently locked.
- When memory is disabled, stop learning and saving new personalization memories and stop using previously stored memories to generate replies.
- While memory is disabled, use the current conversation context and the configured companion settings. Preserve existing memories without deleting them, and make them available again when memory is re-enabled.
- Continue saving conversation history while memory is disabled, but do not store new conversation summaries in personalization memory during that period.
- After memory is re-enabled, resume learning only from new conversation content recorded after re-enabling. Do not retrospectively summarize or extract facts/preferences from messages recorded while memory was disabled. Those messages remain readable in History and may remain part of the current conversation context, but are excluded from persistent-memory learning.
- Apply this rule within a resumed conversation as well as across conversations. Preserve its existing eligible summary and memories, then update them using only eligible new content. Track message-level memory eligibility so a later job cannot accidentally process the entire history including a memory-disabled interval. Re-enabling memory does not remove exclusions for facts the user previously deleted.
- Automatically summarize each conversation and store its summary in memory for use by the personalization model/workflow.
- Conversation history and personalization memory are related but separately addressable product features.
- Deleting a conversation removes its message history but preserves its summary and learned personalization memories. Users manage or delete retained memory separately through the memory controls.
- Generate conversation summaries and automatic personalization updates when the conversation ends or after 15 minutes of inactivity. Periodic summary generation during active conversation is outside the selected initial behavior. This scheduling choice concerns automatic summarization; explicit remember commands remain a separate confirmed capability.
- The 15-minute summary timeout is separate from the short silence detection used to submit each spoken utterance to STT. It does not delete history or prevent resuming the conversation. Precise activity events that reset the timer, the end-of-conversation event, and summary format remain to be specified.
- Maintain one current summary per conversation. When the user resumes a summarized conversation and adds messages, update that same summary at the next conversation-end or 15-minute inactivity trigger, subject to the memory setting. Incorporate the additional discussion rather than creating separate user-visible summaries for each resumed segment.
- Personalization memory contains both conversation summaries and separate, individually manageable facts/preferences. Examples include "prefers short answers" and "interested in music." Each item can be viewed, edited, or deleted independently of the conversation summary.
- Store both forms of memory in Supabase Postgres, scoped to the signed-in account and synchronized across devices. The automatic memory job produces or updates the conversation summary and extracts suitable fact/preference items. Do not blindly duplicate the same learned item when processing another conversation.
- After the user deletes a fact/preference item, do not automatically restore or relearn that information from existing history, retained summaries, or new conversations. Allow it to become persistent memory again only when the user explicitly instructs the AI to remember it again. A new mention alone is not permission to restore it.
- Apply this exclusion to both fact/preference extraction and summary-based personalization. Retained summaries must not provide a route for using the deleted fact as persistent personalization, and future summary updates must not reintroduce it. Do not delete an entire conversation merely because one learned fact was deleted. Current-conversation context remains available under the existing conversation behavior.
- If the user explicitly asks to remember something while memory is disabled, show an action labeled "Enable memory and save this" (localized into Thai/English). Present the specific item to be saved and wait for the user's confirmation. On confirmation, enable memory and save that item; without confirmation, keep memory disabled and do not save it as persistent memory. Do not claim the item was remembered before the save succeeds.
- This confirmation permits saving the requested item from the disabled period as an explicit user action; it does not permit retrospective learning from other messages. For a previously deleted fact, an explicit remember-again request and confirmation lift only that fact's exclusion. Preserve all other deletion exclusions.
- If newly learned information conflicts with an existing fact/preference memory, the AI may update the memory automatically without asking for confirmation, including when the user previously edited that item manually. Manual edits do not permanently lock an item against later learning. Users can inspect and edit the resulting value through Settings > Memory.
- Apply automatic updates only when memory is enabled and the source content is eligible under the existing learning rules. This permission does not override deleted-fact exclusions or allow modification of saved companion personality settings. Update related summary information consistently so personalization does not use conflicting old and new values.
- Do not show notifications for automatic memory creation or updates. Apply these changes silently and make the current summaries and fact/preference items available in Settings > Memory for inspection, editing, and deletion. Do not insert automatic-memory notices into spoken replies or captions.
- This notification preference concerns automatic learning only. Keep the confirmed "Enable memory and save this" action for explicit requests while memory is disabled; its required confirmation is unchanged. Feedback for other user-initiated save/edit/delete actions remains a separate UI detail.
- The exact fact categories and handling of uncertain information remain to be specified. The implementation must define how to track deletion exclusions, recognize equivalent wording, and filter affected summaries without losing unrelated information. Pending-request expiry, cancellation, and failed-save recovery remain to be designed.
- Treat configured personality traits as the normal baseline. The AI may adapt individual replies to the conversation context even when the resulting behavior differs from those settings.
- Contextual adaptation must not overwrite the saved personality settings.
- The remaining priority rules involving explicit in-conversation instructions and learned memories remain to be specified.
- Detailed memory retrieval and how personalization affects voice and text responses remain to be specified.

### Remaining Validation and Review

- Verify the selected OpenRouter model identifiers, audio/streaming capabilities, Thai quality, speaking speeds, caption alignment, latency, and measured usage before committing to paid integration.
- Validate the Next.js/Cloudflare runtime, authentication/email delivery, private-trial authorization, and durable background jobs.
- Review proposed implementation defaults and any material model, scope, or operating-cost change with the owner. Routine visual and engineering details can use the documented proposals rather than another discovery question.

## 2. Pages and Main Features

### Confirmed Page Map

Main navigation contains Conversation, History, and Settings. My Companion and Memory are nested within Settings rather than shown as main navigation destinations.

Use a collapsed navigation menu on both mobile and desktop. A Menu button opens navigation to Conversation, History, and Settings. Keep navigation collapsed by default to preserve the minimalist conversation screen. Exact placement and dismissal behavior remain to be defined.

| Page | Content and actions |
| --- | --- |
| First setup | Begin with an optional AI-led voice interview using saved/default companion settings: three to five core questions plus three optional learning-language questions (approximately six to eight total), with readable text and typed fallback. Start interview explicitly enables eligible voice capture. On completion, save eligible introductory memories automatically when memory is enabled, end the interview session, then suggest a personality preset, gallery image, and voice from available catalogs. The user confirms suggestions, chooses alternatives, or skips customization. Save accepted choices or use existing/default settings and enter a new normal conversation. Keep the interview as separate text-only history. No mandatory preset selection. |
| Conversation | Default ball or locally imported supported rigged 2D model, with AI captions; voice interaction; open the text panel, read both speakers' messages, send typed messages, and open source links attached to web-assisted replies. |
| History | List retained conversations with short topic-based titles and dates, latest accepted user activity first. No search field. Allow manual title renaming and preserve those names through later automatic updates. Confirm individual or multi-select history deletion. Stop a selected active conversation across its sessions before deletion. Open/read text, resume, or delete history while retaining saved personalization memory. No voice replay or Listen again controls. Keep compact active-session controls. |
| Settings | Configure light/dark/system theme, primary accent color, Show AI captions, interface language, manual/automatic voice startup, automatic conversation follow-ups, and a Web search on/off toggle; access My Companion and Memory sections; delete the user's own account after explicit confirmation. Keep active voice-session controls available. Show Trial Access and AI Budget only to the owner. |
| Settings > My Companion | Edit the companion's name; select a personality preset and adjust traits; write, edit, or clear optional additional personality instructions; select a gallery image or import/replace/remove a device-local supported rigged 2D model and return to the default ball; choose a voice, preview it, and adjust speaking speed. Automatically save edits without a Save button and show saving/saved/failure status. Offer Reset personality and a 1,000-character instruction field with a counter. Preview alone does not save a voice selection. |
| Settings > Memory | Use two tabs: Facts/preferences and Conversation summaries. Add a fact/preference directly; view, edit with an explicit Save, and delete items/summaries; disable memory. No user-facing search field. Apply the existing Enable memory and save this confirmation if a new item is submitted while memory is disabled. Developer diagnostics search is limited to the developer's own account and designated test accounts, without a new user-facing dashboard. |
| Settings > Trial Access (owner only) | View permitted/revoked email entries, add an email, revoke access while retaining data, and reinstate access to the same account. Show daily allowances for trial accounts and the owner's account; allow owner-only per-account adjustment for the current UTC day, reverting to the 30-minute default at the next reset. Show the override expiry and preserve used time when editing. Hidden from ordinary users and protected by server authorization; this does not grant access to private conversation or memory content. |
| Settings > AI Budget (owner only) | View current-period AI spending, monthly cap, and remaining budget; raise the cap for the current month only. Show that next month's base cap returns to USD 10. Does not purchase provider credits. |
| Sign In | Google and email/password sign-in for the owner and permitted invitees; verified-email eligibility checks against the allowed list. Registration and recovery details remain to be defined. This is an entry screen rather than a main navigation destination. |

Confirmed feature: personality customization through presets, five-level trait sliders, and optional free-text instructions in Settings > My Companion. Custom text takes precedence for conflicting style preferences. New-account trait values are Medium playfulness, High gentleness, and Short replies. Remaining response-length guidance and other field limits require definition; custom instructions are capped at 1,000 characters under Step 172. These settings guide the response baseline; the AI can still adapt to context without changing saved settings.

Confirmed companion profile: one main companion initially named Laven, with an editable name, adjustable personality, and changeable image selected from the app's gallery. The product name remains Laven AI independently of the user's companion-name changes.

Confirmed feature: automatic learning from conversations plus explicit "remember this" commands.

Confirmed memory-management actions in Settings > Memory: view, edit, and delete individual fact/preference items; view, edit, and delete conversation summaries; disable memory. Present Facts/preferences and Conversation summaries as two tabs within this section, confirmed in Step 169. Do not show a search field to users, confirmed in Step 168; this removes search only, not their memory-management controls. Developer-only search is restricted to the developer account and designated test accounts under Step 173, using scoped local diagnostics rather than another dashboard. Do not infer authorization to search other invitees' private content or add such access to owner administration. Exact layout, button labels, and disabled-state behavior remain to be defined.

Confirmed automatic-memory presentation: no notices when the AI creates or updates memory. Users inspect and manage the resulting memory in Settings > Memory. This does not remove confirmation controls for explicit actions that require them.

Confirmed owner administration: Settings > Trial Access lists email entries with their permitted/revoked status and provides Add email, Revoke access, and Reinstate access actions. Revocation retains the user's account data; reinstatement restores access to that data under the same account. Ordinary invitees cannot see or use this section. Owner administration grants trial-eligibility management; it does not grant an application feature for reading other users' private conversations or memories. Detailed layout and validation messages remain to be defined.

Confirmed conversational memory action: when memory is disabled and the user explicitly requests a save, offer an "Enable memory and save this" button showing the requested item. Wait for confirmation before changing the setting or saving. This action must be accessible from the conversation screen in both voice and typed interactions, without requiring navigation to Settings.

Confirmed voice feature: offer both continuous conversation and button-activated speaking, with continuous conversation selected by default.

Confirmed button-mode control: hold the microphone button while speaking, then release to stop recording and submit that utterance. This controls a spoken turn, not the lifetime of the overall voice session. Keep Stop session as a separate action.

During an active continuous session, pressing the microphone control mutes only local microphone input, confirmed in Step 123. Show a clear muted state and allow the user to unmute without creating a new session, resetting quota, or adding a greeting. Muting stops new microphone capture/submission but does not cancel an already accepted reply, stop its speech, or pause elapsed-session quota. Typed input remains available and keeps its existing interruption behavior. Keep Stop session separate so users can end the session and its elapsed-time accounting. Other sessions remain independent. Hold-to-talk retains its distinct hold/release microphone behavior.

If mute is pressed before captured audio has been submitted for transcription, discard that unfinished utterance and its transient audio buffers, confirmed in Step 143. Cancel the pending two-second utterance-end timer so it cannot submit discarded audio after mute. Do not create a user-message entry, call STT, or generate a reply from that discarded recording. Unmuting begins fresh capture without restoring the discarded audio. Audio already submitted follows the accepted-turn workflow; mute alone does not cancel it. Validate ordering at the mute/submission boundary to prevent a stale capture callback from submitting the discarded utterance.

Confirmed main screen elements: central lavender circle with subtle listening/thinking/speaking animations and a customizable image, microphone control, captions beneath the visualization, and access to the conversation text. Detailed button actions and layout remain to be specified.

Confirmed persistent voice controls: while an active voice session continues in History or Settings, show a compact control bar on mobile and desktop. Provide the current listening/thinking/speaking state, a visible microphone-muted indicator when applicable, remaining daily allowance, Stop session, and Return to conversation. Returning to Conversation reuses the existing session and its mute state. Voice previews pause the local conversation under Step 150. Bar placement and interaction with conversation switching remain to be designed.

When the user requests a voice preview in Settings, pause any active voice session on that surface before playing the sample, confirmed in Step 150. Stop local microphone capture, conversational speech/captions, and proactive follow-ups; suspend active-session elapsed-time accounting while formally paused. Discard unsubmitted recording buffers and cancel their pending submission timer. Prevent preview audio from being transcribed as user input or late conversational audio from playing over the sample. Keep the existing conversation and accumulated usage, and leave other surfaces' sessions independent. After sample completion, cancellation, or failure, remain paused and offer explicit Resume with the normal permission, access, daily-allowance, and monthly-budget checks. Do not automatically restart listening, create a new conversation, or replay interrupted speech. Use transient preview audio only and respect shared AI-budget controls. Voice-preview playback is exempt from daily conversation-time deductions under Step 151. Cancel unfinished local accepted work when preview starts under Step 152; cancellation and synchronization at the pause boundary require validation.

Confirmed appearance settings: light/dark/system theme and user-selectable primary accent color, with lavender purple as the default.

Confirmed circle-image customization: select a ready-made image from the app's gallery. Gallery interface and exact selection controls remain to be defined.

Confirmed text conversation feature: show messages from both speakers and provide a text input plus a Send button for typed messages. Every AI reply to a typed message is delivered as both text and speech.

Confirmed voice customization: a library of selectable voices, a Preview button to hear a voice sample before selecting it, and three speaking-speed choices: Slow, Normal, and Fast, confirmed in Step 161. Voice previews use only the selected interface language: Thai for the Thai interface and English for the English interface, confirmed in Step 153. Do not include both languages in a single preview by default. New accounts start with Normal speed under Step 171. Available voices, sample wording/duration, and actual speed values remain to be defined or validated.

Starting a voice preview cancels unfinished STT/reply generation for the local already-submitted turn, confirmed in Step 152. Preserve user/AI text already saved, mark an unfinished reply or turn as interrupted, and do not create an empty AI message merely to display cancellation. Request upstream cancellation where supported; reject late transcripts, reply text, and audio from that cancelled turn. Clear its pending retries, speech requests, and transient audio so nothing resumes behind the preview or when Resume is pressed. Keep other surfaces' independent turns and eligible background memory jobs unaffected. Resume returns to the existing conversation and requires new user input to continue that cancelled exchange; it does not automatically resubmit the old question. Provider cancellation and turn-state ordering require validation. Ordinary completed replies still use text and voice; no text-only completion exception is selected.

### Conversation History and Summary Memory

- Save conversation history automatically.
- Provide a history page where the user can open a saved conversation, read its messages, listen again to an AI reply, resume the conversation, or delete it.
- Generate a summary for each conversation when it ends or after 15 minutes of inactivity, and store it in memory for personalization. Process this in the background.
- Summary-memory storage and updates are subject to the memory setting: do not create or update personalization summaries while memory is disabled.
- Re-enabling memory does not trigger processing of messages from the disabled period. Continue saving and displaying that history independently; future summary updates exclude those messages.
- Keep one current summary per conversation. After a resumed conversation receives additional messages, revise its existing summary at the next eligible summary trigger. Keep the conversation history available for resuming independently of its summary.
- The Delete conversation action removes message history while retaining the conversation's summary and learned personalization information.
- Automatically delete a conversation's message history after seven days without a new user turn in that conversation. Each accepted spoken or typed user message restarts the retention clock for that entire conversation, preserving its existing messages until the new expiry. Use server timestamps and a seven-day elapsed duration, independent of daily/monthly quota resets.
- For a newly created conversation that has not received a user turn, use its creation timestamp as the initial retention anchor so greeting-only threads can expire. AI greetings and follow-ups do not extend that anchor.
- Reading history, opening the conversation, background summaries, and proactive AI follow-ups alone do not restart the retention clock. Apply the clock across the shared conversation's concurrent sessions, rather than separately per device. History that has already expired cannot be recovered merely by starting another conversation.
- Automatic history expiry preserves existing conversation summaries and learned fact/preference memories, which remain separately manageable in Settings > Memory. Discard any transient audio associated with expired source messages; expired text is no longer available for reading or resuming as message context. Retention cleanup must not bypass disabled-memory or deleted-fact exclusions, or use expired messages to complete stale learning jobs.
- Retained summaries and learned information remain manageable through the memory controls, including editing and deletion.
- Alongside each conversation's current summary, maintain individually manageable fact/preference memories for personalization. Fact/preference items can be used across conversations within the same account; exact retrieval and source-link representation remain to be designed.
- Persist conversation text without storing user recordings or generated AI audio for later playback. Generated speech requires only transient processing/playback buffers, which are discarded after the attempt completes or is cancelled. History is text-only with no voice replay, confirmed in Step 112. New replies still use the selected text-and-speech flow.
- Concurrent sessions add messages to one shared conversation history and use one current summary for that conversation. Do not create separate history or summary records merely because another device or tab joins the session.
- The seven-day retention duration and conversation-level clock based on the latest user turn are confirmed. History uses short topic-based conversation titles with dates, confirmed in Step 113. History has no search field, is ordered by latest accepted user activity, and permits manual title renaming and multi-select deletion under Steps 163–166. Title-generation timing, budget checks, temporary date/time fallback, and how retained memory is represented after its source history is deleted remain to be defined; preserve manually saved titles, confirm deletion, and stop a selected active conversation before deleting its history under Steps 175, 176, and 178. Cleanup scheduling and backups/provider retention require separate implementation review; do not present this product rule as verified deletion from every external system.

To define together: detailed page layouts, remaining button behavior, navigation presentation, and account lifecycle flows.

## 3. Folder Structure

Planned application root: `C:/Users/phetm/Documents/Codex/2026-09-30/cha/work/laven-ai`. The tree below is relative to that project root. Planning artifacts remain in `outputs/`. No application source has been created at this checkpoint. The current foundation checklist is `outputs/executor-brief-02-production-foundation.md`; Brief 01 is superseded. Use `outputs/task-backlog.md` for bounded assignments and `outputs/progress_tracking.md` for their current status.

Use the following planned structure for the selected Next.js/TypeScript application. These paths describe future implementation; application code and services have not been created yet. The specification remains in `outputs/blueprint.md`.

```text
project-root/
  outputs/blueprint.md           # English specification and discovery decisions
  src/
    app/
      layout.tsx                # Shared application shell
      globals.css               # Themes, lavender accent, global styles
      (auth)/
        sign-in/page.tsx        # Google and email/password sign-in
        auth/callback/route.ts  # Authentication callback handling
      (main)/
        layout.tsx             # Persistent voice-session shell across main pages
        conversation/page.tsx   # Voice circle, captions, expandable chat
        onboarding/page.tsx     # Optional AI-led introduction interview and companion setup
        history/page.tsx        # Read, resume, and delete history
        settings/
          page.tsx              # Appearance, language, voice-mode preferences
          companion/page.tsx    # Companion name, personality, gallery, voice
          memory/page.tsx       # Inspect, edit, delete, disable memory
          trial-access/page.tsx # Owner-only allowed-email management
          ai-budget/page.tsx    # Owner-only monthly AI budget controls
      api/
        transcribe/route.ts     # Authenticated completed-utterance STT
        reply/route.ts          # Context assembly and regular LLM generation
        speech/route.ts         # TTS and voice previews
        conversations/         # History and summary scheduling endpoints
        memory/                # Memory management endpoints
        admin/trial-access/    # Owner-authorized allowlist endpoints
        admin/daily-allowance/ # Owner-authorized per-account daily allowance settings
        admin/ai-budget/       # Owner-authorized budget configuration endpoints
        usage/                 # Account allowance and usage status
    components/
      voice/                   # Word-progress captions and session controls
      avatar/                  # Ball, imported 2D renderer, local import controls
      chat/                    # Messages, text input, desktop/mobile panels
      settings/                # Personality, voice, theme, memory controls
      ui/                      # Shared buttons, dialogs, menu, form controls
    hooks/                     # Voice session and synchronized UI state
    lib/
      audio/                   # VAD, recording, playback, interruption handling
      avatar/                  # Local validation/storage, runtime adapter, state mapping
      ai/                      # OpenRouter clients, model IDs, prompt builders
      supabase/                # Browser/server clients and session utilities
      personalization/         # Memory retrieval and summary processing logic
      jobs/                    # Queue messages and job scheduling utilities
      usage/                   # Voice allowance and shared AI budget enforcement
      i18n/                    # Thai/English interface strings
      validation/              # Request and settings validation
    types/                     # Shared application and generated database types
  public/
    gallery/                   # Bundled licensed images; never user-imported packages
    icons/                     # Application icons
  supabase/
    migrations/                # Versioned database changes and access policies
    seed.sql                   # Non-sensitive development data, if needed
  workers/
    summary/                   # Proposed queue consumer for memory jobs
  tests/                       # Critical account, voice, and memory workflows
  docs/                        # Deployment, operations, acceptance criteria
  wrangler.jsonc               # Cloudflare Worker settings and bindings
  .env.example                 # Variable names only; no real credentials
  .gitignore                   # Exclude secrets, local environment files, and generated/private data
  package.json
  tsconfig.json
```

Keep AI provider access and privileged database operations in server-only modules. The browser owns recording, VAD, playback, and UI state. Database migrations remain versioned independently of UI components. The deployment adapter and its additional configuration files will be finalized after a Workers-runtime compatibility check. The separate summary worker is proposed alongside Cloudflare Queues; conversation end or 15 minutes of inactivity is the selected trigger, with its detection mechanism still to be defined.

## 4. Voice and AI Behavior

### New Conversation Greeting

- When a new conversation starts in an eligible voice session, have the AI give a short greeting first, following the configured personality, then leave room for the user to speak. Show and speak the greeting as an AI message, using the normal captions, audio routing, usage checks, and history rules.
- Generate one opening greeting per new shared conversation, not one per joining device. Play it on the surface initiating that conversation and synchronize its text to other surfaces. Joining an existing conversation or resuming a paused session does not create a duplicate opening greeting. Reuse the normal interruption behavior when the user speaks or sends a message during the greeting.
- Personalize the opening greeting using relevant saved interests or preferences when memory is enabled. Apply the same eligibility, deleted-fact exclusions, and no-backfill rules used for other replies. Do not retrieve personal memory while memory is disabled. If no suitable memory is available, use a general greeting in the configured personality.
- Keep personalized greetings brief and grounded in saved information; do not invent recent events or imply that the user has done something merely because a past interest is remembered. Before the user's first spoken or typed input in a new conversation, greet in the selected interface language, confirmed in Step 155. Use this language even when eligible memory suggests a different language from past conversation. Once the user provides input, apply the existing automatic Thai/English and mixed-language response rules, including explicit supported-language requests. This changes neither the saved interface language nor the existing memory eligibility and originating-surface audio rules.

### Confirmed First-Release Web Search

- Include web search in the first release using Parallel Fast through OpenRouter. Proposed integration: `openrouter:web_search` with `engine: parallel` and `mode: fast`. Preserve the selected Gemini conversation model and the STT/LLM/TTS architecture. Do not silently use Auto, Parallel Basic/Turbo, Exa, or native Google search instead of the selected engine/mode.
- Provide a Web search on/off toggle in Settings for each account and synchronize the preference across its devices. Default it to off for new accounts; users enable it explicitly in Settings. When disabled, prevent new search calls for that account and keep ordinary companion conversation available under existing access and usage checks. Enforce the saved preference on the server rather than merely hiding a browser control; the AI must not silently enable search itself.
- Enabling search makes it available when useful rather than requiring a search on every turn. Query-data minimization, call limits, and in-flight toggle changes require definition and validation. Search fees and additional model processing count toward the existing shared USD 10 monthly budget; no increase is selected.
- Validate Parallel Fast's Thai, English, and mixed-language results with the chosen OpenRouter model route. Fast's language availability remains undocumented in the reviewed guide, so Thai support is not a verified app capability. No paid prototype tests have been run. This choice does not authorize integrations that send messages or perform external actions on the user's behalf.
- Show clickable source links for web-assisted replies only in the chat panel, associated with the relevant AI message and retained with it in History until expiry or deletion. Do not insert automatic source-name announcements or read URLs aloud. Keep citation metadata separate from the speakable reply so TTS and speech-progress captions do not pronounce link labels or citation markers. Source references must map to retrieved results rather than invented links; exact rendering and source-grounding validation remain implementation details.
- Limit web search to ten actual search calls per account per UTC calendar day, shared across devices and sessions. Reset at 00:00 UTC (07:00 in Thailand). Count search executions rather than user questions; a question that makes multiple searches consumes multiple calls. Enforce remaining allowance on the server, including concurrent requests.
- At daily search exhaustion, prevent further searches and display the next reset time. Allow ordinary conversation without new web searches when the account's voice allowance, monthly budget, and access eligibility still permit it. Do not describe an answer as freshly web-verified when no search ran. The search toggle remains a saved preference rather than silently switching off at exhaustion.

### Web Search Cost Review - October 2, 2026

Current OpenRouter search fees, excluding model tokens:

| Engine/mode | Per search call | 100 calls | 1,000 calls |
| --- | --- | --- | --- |
| Parallel Fast/Turbo | USD 0.001 | USD 0.10 | USD 1.00 |
| Parallel Basic/Advanced | USD 0.005 | USD 0.50 | USD 5.00 |
| Exa Instant/Fast/Auto | USD 0.007 | USD 0.70 | USD 7.00 |

These modes include up to ten results per call; additional results cost extra. Parallel Turbo lists English/Japanese availability, Fast's language support is undocumented, and Basic/Advanced list broad language support. Thai quality still needs validation. Prefer the current `openrouter:web_search` server tool over the deprecated web plugin or `:online` suffix. One user question can trigger multiple charged search calls. [OpenRouter current search guide](https://openrouter.ai/docs/guides/features/server-tools/web-search).

Illustrative extra model input: 2,000 additional processed tokens per search at the selected current Flash input rate of USD 0.75/million adds USD 0.0015 per search, or USD 0.15 per 100 searches. This excludes additional output/thinking, longer audio, repeated context processing, and funding fees. At 150 monthly searches, selected Parallel Fast fees plus that illustrative extra input total USD 0.375; Basic totals USD 0.975 and Exa USD 1.275 as comparisons, on top of the voice pipeline. These are assumptions, not measured bills. [Google Flash pricing](https://ai.google.dev/gemini-api/docs/pricing).

Google's native grounding separately lists USD 14 per 1,000 searches after its direct-API free allowance. Do not assume that allowance transfers to OpenRouter. Native search is not the chosen route: Step 92 selects Parallel Fast. Search must fit the existing shared USD 10 budget unless the owner changes that policy.

### Confirmed Voice Modes

- Continuous conversation is the default selected voice mode. After the user starts a session, they can talk back and forth without pressing a button for each turn, and interrupt the AI while it is speaking.
- The alternative voice mode uses hold-to-talk: record the spoken turn while the microphone button is held, and stop recording and submit the completed utterance when it is released. Do not submit audio from outside the held interval. Support the same hold/release behavior on mobile touch and desktop pointer input; provide an accessible keyboard equivalent without intercepting typing in the chat input.
- Releasing the microphone button ends the spoken turn, not the overall voice session. In this mode, an active session's pauses between turns still consume elapsed-session daily allowance. Stop session remains a separate control. Pointer cancellation, empty recordings, and interruption handling while holding the button are implementation details to resolve.
- Users can switch between the two voice modes. A mode change during local AI speech stops that speech and switches immediately, confirmed in Step 114. Clear the local playback queue, transient audio buffers, and captions for the interrupted speech, and prevent late audio from restarting it. Preserve the saved reply text, shared conversation, existing session, and continuous daily-quota accounting without duplicating the reply. Do not stop other surfaces' independent sessions or speech because this surface changed mode.
- If a mode change occurs after audio submission while STT or reply generation is running but before local AI playback begins, switch input mode immediately and let the accepted turn continue to its normal text-and-speech reply, confirmed in Step 145. Do not restart transcription, duplicate the turn, or cancel generation solely because the input mode changed. Preserve originating-surface audio routing, conversation/session identity, mute/pause state, and usage accounting. Subsequent input uses the newly selected mode. Speaking or sending a new message still interrupts under Step 122; access revocation, disconnection, exhaustion, and explicit stopping retain their existing controls. Validate the transition into playback so a switch that actually occurs during speech follows Step 114 instead.
- When switching modes during local capture before STT submission, discard the unsubmitted utterance and switch immediately, confirmed in Step 144. Release its transient recording buffers, cancel any pending utterance-end timer, and invalidate old capture callbacks or hold-button release events so they cannot submit discarded audio. Do not call STT or create a message/reply from that recording. Preserve the shared conversation, existing session, and accumulated usage without pausing or resetting active-session accounting solely for the mode change. Continuous mode begins fresh capture only when the session is active, input is unmuted, and permissions/access/usage allow it; hold-to-talk requires a fresh press. Do not automatically unmute or resume a paused/stopped session. Capture/submission ordering and mode-control state require validation.
- Provide a session-start preference with two options: press Start conversation to begin, or start listening automatically when the conversation page opens after microphone permission has been granted.
- Synchronize this start preference with the account's other settings.
- Automatic listening on entry to the Conversation page is the initial session-start preference. Start only after microphone permission is granted, the authenticated account is eligible, and daily allowance and shared AI budget remain available. Begin elapsed-session quota accounting when the voice session actually starts, not merely when the page loads or while waiting for permission.
- Keep manual Start available through the saved preference and as a fallback when automatic startup is unavailable. Honor an explicit Stop while the user remains on the page; do not immediately restart listening because automatic startup is selected. Continuous conversation remains the default interaction mode independently of the startup preference.
- Preserve an active voice session when navigating within the app from Conversation to History or Settings. Continue listening, speaking, and elapsed-session quota accounting, and expose compact controls including Stop. Returning to Conversation must reuse the active session without duplicate microphone capture or a new quota timer.
- Concurrent sessions are supported across devices/tabs and join the account's shared active conversation. Give each session independent microphone capture, interruption handling, and lifecycle. Stopping or interrupting one session does not automatically stop the others; account-wide access or usage exhaustion still applies to every session.
- Play each AI reply's audio only on the device/tab that submitted the corresponding spoken or typed user turn. Other surfaces receive the shared text only, even when they have active voice sessions. Track the originating surface/session for each turn and route audio accordingly. Shared text synchronization must not trigger automatic speech playback on receiving surfaces.
- The active companion's speaking state and AI captions follow local audio playback. Do not show a remote reply as locally speaking merely because its text arrives in the shared chat. Other devices may continue their own session listening while displaying the synchronized text. Recovery when the originating surface disconnects remains to be designed.
- Ordinary navigation does not change which conversation receives the active session's messages or end that conversation merely because another page is viewed. Explicitly starting another conversation or resuming a different history thread switches all active sessions to the selected shared conversation, as confirmed in Step 89. When switching browser tabs/apps or locking the screen, attempt to continue the current voice session where the browser and device permit it, with a paused-state fallback when continuation is unavailable. Background capture, playback, interruption, and reliable quota accounting require device testing; do not promise uninterrupted background or locked-screen operation. Disconnection and closure recovery remain to be specified.

### Floating Companion - Historical Feasibility Notes Updated by R001

- Historical October 1 scope deferred floating delivery. R001 confirms Windows floating in the first release; T078 must verify the Windows version/runtime/packaging matrix. Framework, packaging, and OS integration remain unselected. The historical browser notes below are reference only and require re-verification.
- Confirmed future content: a customizable companion picture, session status, captions, and pause/resume and stop controls. Make the control menu collapsible so users can hide it and reveal it again. Hiding controls must not pause or stop the conversation. Exact default visibility and layout remain design details.
- Use the same default ball or supported locally imported 2D model and existing gallery options. Browser and native local stores are not automatically shared; require a separate import rather than transmitting assets.
- Browser feasibility reference only: a compact Document Picture-in-Picture window can contain the companion image and interactive HTML controls. This API supports an always-on-top window above other windows, not just a video. Chrome and Edge desktop are possible validation targets if a browser preview is considered later. This is not a selected first-release implementation or a tested capability of this app. [Chrome Document PiP documentation](https://developer.chrome.com/docs/web-platform/document-picture-in-picture/).
- The reviewed MDN compatibility data lists Chrome desktop support from version 116, Edge support through the Chrome mirror, and Firefox support from version 151. Chrome Android, Firefox Android, Safari, and Safari iOS do not support this API in the reviewed data. Feature-detect the actual runtime instead of assuming availability from the device name. Proposed unsupported-browser fallback: a floating companion inside the app page, which cannot stay above other apps. [MDN compatibility data](https://github.com/mdn/browser-compat-data/blob/main/api/DocumentPictureInPicture.json).
- If a browser PiP version is pursued later, propose an explicit Open floating companion action. Normal Document PiP opening requires user activation; automatic opening is a separate capability with additional browser eligibility conditions and has not been selected. The window cannot outlive its opener, and the website cannot set its screen position. A browser PiP window does not establish support for a frameless, transparent, freely positioned system-wide icon or locked-screen UI. Those desktop-software requirements need separate validation. [Chrome Document PiP documentation](https://developer.chrome.com/docs/web-platform/document-picture-in-picture/), [MDN API overview](https://developer.mozilla.org/en-US/docs/Web/API/Document_Picture-in-Picture_API).
- In the future implementation, the floating view must control its existing local voice session rather than start a second microphone capture or quota timer. Use the same conversation, local audio, saved companion configuration, and limits. Opening it must not restart a paused or explicitly stopped session. Caption layout, desktop integration, and behavior when the floating window closes require later design and prototype validation.

### Proactive Conversation During Silence

- Enable automatic conversation follow-ups by default for new accounts. Provide an on/off toggle in Settings, synchronized with the account's other preferences. Turning it off cancels pending silence-triggered follow-ups without ending the voice session; ordinary replies to user input remain available under the existing access and usage rules.
- In an active continuous voice session, allow the AI to initiate a follow-up after 30 seconds of user silence, such as a natural question about the current topic. After local AI speech finishes, wait 30 seconds without new user speech or a sent message before initiating the follow-up.
- If the user does not answer the first proactive follow-up, allow one additional follow-up after another 30 seconds of silence measured from the end of its speech. Limit the sequence to two unanswered proactive follow-ups total. After the second follow-up finishes speaking, wait a further two minutes without user input, then automatically pause that local session. Count active session time during the wait; stop microphone capture, silence-triggered follow-ups, and session-time quota accounting when the pause takes effect.
- Show a paused state with an explicit Resume conversation action. Preserve conversation history and settings. Do not automatically resume microphone listening because automatic startup is enabled; Resume must recheck permission, account access, daily allowance, and monthly budget. Pausing one session does not automatically pause the account's other active sessions. The existing 15-minute summary inactivity rule remains separate.
- This behavior requires an active continuous session and must stop when that session is stopped or access or usage limits prevent conversation. It does not authorize messages or notifications outside an active session, or proactive speech in hold-to-talk mode.
- Do not trigger a silence follow-up while user input, reply generation, or speech playback for that session is in progress. Treat the proactive prompt as another AI turn with the normal saved personality, memory rules, shared conversation history, and budget checks. Active-session elapsed time continues to count toward the daily allowance.
- Define coordination across concurrent sessions so silence on one surface does not create duplicate or competing follow-ups in the shared conversation or bypass the two-follow-up limit. Selection of the originating session for proactive audio and precise activity/timer coordination remain to be specified. Background continuation is selected in Step 78, subject to runtime support and a paused-state fallback.
- The proactive silence timer is distinct from utterance-end detection for STT and the 15-minute summary timeout. Do not implicitly change either existing rule by adding this feature.
- Automatic silence-triggered follow-ups continue while the microphone is manually muted, confirmed in Step 124, provided the saved proactive-follow-up toggle is enabled and access/usage checks allow them. Apply the same 30-second waits, maximum of two unanswered follow-ups, and automatic local pause two minutes after the second finishes without new input. Sent typed messages count as user input under the existing timer/reset rules. Muting alone keeps elapsed-session quota running; when the automatic pause takes effect, elapsed-session quota stops and explicit Resume is required. Do not unmute the microphone merely to deliver a follow-up. The saved account-level proactive-follow-up toggle is unchanged.

### Confirmed Conversation Languages

- At launch, support Thai and English with automatic language switching based on the user's spoken or typed input.
- Support conversations in which the user mixes Thai and English, with the AI adapting its response language to the conversation.
- Add Chinese and Japanese in a later phase. The Chinese language variety and writing system remain to be defined before that phase.
- Conversation language follows the user's spoken or typed input independently of the selected interface language, confirmed for typed messages in Step 154. Adapt to Thai, English, and mixed Thai-English input without changing the saved interface language. Honor an explicit request to reply in a supported language rather than mechanically matching the language of the request's wording. Ordinary typed replies still produce both text and speech, with originating-surface audio routing and normal interruption, memory, access, and usage controls. The available voice catalog and actual multilingual speech quality remain to be validated.

### Confirmed Voice Customization

- Users can choose from a library of voices.
- Users can preview a voice sample before selecting it. Use the current interface language for that sample under Step 153, independently of the conversation's detected language. A preview does not change the selected interface language or the companion's saved voice. Validate actual Thai/English pronunciation and route support before accepting a voice into the selectable catalog.
- Voice samples use expressive delivery based on the companion's currently saved personality, confirmed in Step 162. Derive delivery guidance from the saved preset, traits, and custom personality instructions with the existing style-precedence rules, while keeping the sample in the selected interface language. Do not apply unaccepted onboarding suggestions or failed autosave drafts as saved personality. This is a preview of companion delivery, not a memory-learning turn; no personal-history retrieval is required. Mapping settings to TTS delivery instructions and actual expressive quality still need validation. Previewing does not change settings, and normal preview pause/cancellation, monthly-budget, and transient-audio rules remain in effect.
- Users can adjust speaking speed through three labeled choices: Slow, Normal, and Fast, confirmed in Step 161. Localize these labels for Thai and English. Autosave the selected choice and retain the current spoken reply's existing speed under Step 157. Define and test distinct provider speed values for the three choices; Normal is the new-account default under Step 171; numeric speed values and provider support remain pending. Do not display a speed adjustment as working if the chosen route ignores or rejects it.
- Saving a different voice or speaking speed while AI is speaking does not interrupt or regenerate the current reply, confirmed in Step 157. Keep the existing voice and speed for all remaining sentences of that spoken reply, including sentences whose audio has not yet been synthesized. The next reply uses the latest successfully saved values, without requiring a new conversation. Keep a consistent transient voice/speed baseline per spoken reply and validate its capture timing, account-setting synchronization, provider speed support, and caption alignment. Do not add retained audio/style snapshots or historical replay. Explicit preview actions still pause the session and cancel unfinished local processing under Steps 150–152; saving settings alone does not trigger preview behavior.
- The AI's emotional speech tone follows both the configured personality and the conversation context, adapting to suit playful, gentle, or serious moments.
- Treat expressive tone as desired product behavior. Its implementation and achievable control depend on the later model discussion and technical validation.

### Word-by-Word Caption Implementation Review - October 1, 2026

Confirmed visual requirement: start on one row, reveal words progressively within the current sentence, and wrap to additional rows as needed. Retain the sentence's revealed words until its spoken completion, then remove all its rows before the next sentence begins. Step 68 supersedes the earlier strict single-line requirement. Sentence transitions follow speech rather than the arrival of generated LLM text. Captions must stay aligned when speaking speed changes, speech is interrupted, or audio is retried.

OpenRouter's reviewed TTS guide describes a raw audio response and does not document word timestamps for the selected route. The reviewed Gemini Flash-Lite TTS model page also does not establish word-timing metadata. Therefore accurate per-word synchronization remains a prototype validation requirement, not a verified provider capability. [OpenRouter TTS guide](https://openrouter.ai/docs/guides/overview/multimodal/tts), [Google selected TTS model](https://ai.google.dev/gemini-api/docs/models/gemini-3.8-flash-lite-tts).

Validate a timing/alignment strategy against actual generated Thai, English, and mixed-language speech before accepting this feature. Do not silently substitute a constant-speed typewriter animation for verified speech alignment. Any additional inference used for alignment must be accounted for in the shared AI budget; no extra provider or model change has been selected.

### User Speech Storage

- Save the user's transcribed text in conversation history, without a persistent archive of the user's recorded speech. Do not add a user-recording playback feature to History for the first release.
- User audio is still needed temporarily for capture and submission to the selected STT route. Release temporary app-held recordings when transcription processing and any bounded retry are complete. Temporary-buffer lifetime, failure cleanup, and provider-side data handling require implementation review; this app storage decision is not a promise about provider retention.
- Generated AI speech is not stored for reuse, following the owner's revised Step 110 decision. Only transient processing/playback buffers are permitted.

### AI Speech Without Storage and Text-Only History

- Do not keep a reusable AI-audio cache, including an in-memory replay cache, browser storage, server files, or an audio archive. The owner revised Step 110 to request no audio storage. Retain only transient buffers required to generate, transport, decode, and play the current attempt, and release them after completion, cancellation, or failure. Do not log audio payloads. This is an app-side storage policy; provider retention requires separate verification. Seven-day text-history retention remains unchanged.
- Do not offer voice replay, Listen again, or regeneration controls on historical messages, confirmed in Step 112. Opening or resuming history displays the old messages as text without playing them. New replies after resumption still produce text and speech through the ordinary conversation pipeline. The previously selected Listen again feature and its replay voice-setting policy are superseded.
- Preserve the existing manual Retry audio action only for recovery of the current reply's failed speech attempt; it is not a playback feature for historical messages. Recheck access, daily allowance, and shared monthly budget before regeneration and playback. TTS regeneration consumes AI budget, and playback follows the existing quota-accounting rules.
- Isolate transient audio processing by account and discard associated buffers when source messages are deleted, the user signs out, or the account changes. Keep only text as retained conversational content; do not save original per-reply voice, speed, or expressive-style snapshots for replay. Existing account-level companion settings, separately managed personalization memory, and necessary history/source-link metadata remain part of their previously selected features.

### Confirmed Transcription and Text-Reply Failure Recovery

- For a recoverable user-speech transcription or text-reply generation failure, retry that failed stage automatically once. If the retry also fails, display a clear error and a manual Retry action. Do not automatically retry account-access denial, exhausted quota/budget, cancelled work, or invalid input. This is separate from the already selected manual Retry audio behavior for TTS/playback failures.
- Retry the existing turn without duplicating user or AI messages. Reuse a successful transcript when retrying only text generation. Check whether the prior attempt already completed before issuing another request, and reject stale work after a conversation switch, stop, or deletion state change. Recheck access and usage limits before any new provider call.
- Keep the current recording available only temporarily for its bounded transcription attempts. If it is no longer available when a manual retry is requested, offer re-recording rather than implying the discarded recording can be recovered. Error classification, temporary-buffer cleanup, and uncertain provider completion require implementation validation; no promise of free retries or provider-level idempotency has been made.

### Confirmed Network Interruption Recovery

- When a local voice session loses connectivity, pause recording and elapsed-session quota accounting, show a disconnected/paused state, and preserve already saved conversation messages. Pause local speech and clear obsolete speech-progress captions. Reconcile session state on the server rather than relying only on a client timer; connectivity detection and exact metering boundaries require runtime validation.
- When connectivity returns, remain paused and show an explicit Resume conversation action. Do not automatically restart microphone listening or speech, even when automatic startup is enabled. Before Resume, recheck microphone permission, account eligibility, daily allowance, monthly budget, and the current shared conversation state. This resumes the existing session rather than automatically creating a new thread or opening greeting.
- Keep the account's other connected sessions independent. Network recovery must not override an explicit Stop, another pause reason, account revocation/deletion, or exhausted usage limits. Reconcile completed turns before retrying so reconnection does not duplicate saved messages or replay old audio automatically.

### Reply Audio Failure Recovery

- Show the available reply text in the conversation text UI and a clear local audio-failure state with "Retry audio." Do not mark the circle as speaking or display speech-progress captions while no audio is playing. Keep the shared text reply and history intact.
- For the manual Retry audio action after a failed speech attempt, regenerate speech from the same saved reply text using the selected TTS model. The revised no-storage policy does not retain failed-attempt audio for later reuse. Do not regenerate the LLM answer solely to repair audio and do not duplicate the shared chat message.
- Route retry audio to the surface performing the recovery action; ordinary shared-message synchronization still must not broadcast speech. Recheck account access, daily allowance, and shared monthly budget before retrying. TTS regeneration consumes AI budget, and actual playback follows the existing daily-quota accounting rules.
- This is an available-text fallback for speech failure, not permission to continue conversation after quota/budget exhaustion or a permanent change to a text-only reply mode. Playback permission handling, retry error presentation, and bounded transient-buffer cleanup remain implementation details. Follow the revised no-storage policy for generated audio.

### Owner-Selected Models and Integration Review

The following identifiers reflect the owner's latest model selections. They supersede the earlier broad TTS reference, initial batch LLM identifier, and earlier live-STT selection. Use OpenRouter for all AI stages, including standard completed-audio transcription in both voice modes.

Use standard Gemini 3.8 Flash inference for both interactive replies and background summaries/memory updates. Background work is scheduled by the application and calls the regular API; it does not use the provider's Batch API. Exact request format depends on the serving provider.

| Role | Currently selected identifier | API route |
| --- | --- | --- |
| Text-to-speech | `google/gemini-3.8-flash-lite-tts` | OpenRouter |
| Conversation and summary/memory LLM | `google/gemini-3.8-flash` (standard inference) | OpenRouter |
| STT, continuous conversation | `google/gemini-3.5-transcribe` after each detected utterance ends | OpenRouter |
| STT, button-activated speaking | `google/gemini-3.5-transcribe` | OpenRouter |

Documentation reviewed on September 30, 2026:

- Google documents `gemini-3.8-flash-lite-tts` with expressive speech, voice-library support, and delivery instructions through `speech_metadata.style`. Its displayed supported-language table includes English but does not list Thai. Thai output support and quality must be resolved before accepting it for the confirmed Thai-English conversation experience; absence from the table alone is not proof that a request cannot work. [Google TTS model documentation](https://ai.google.dev/gemini-api/docs/models/gemini-3.8-flash-lite-tts).
- Google documents the standard `gemini-3.8-flash` model. Owner-confirmed routing: use standard inference for interactive conversation and for application-scheduled background conversation summarization and memory processing. [Google LLM model documentation](https://ai.google.dev/gemini-api/docs/models/gemini-3.8-flash).
- Latest owner-confirmed STT routing (October 1, 2026): use `google/gemini-3.5-transcribe` through OpenRouter in both voice modes. In continuous mode, detect speech and utterance completion locally, then submit the completed audio. In button mode, submit audio when the user ends the spoken turn. [Google STT model documentation](https://ai.google.dev/gemini-api/docs/models/gemini-3.5-transcribe).
- Keep model IDs configurable and use OpenRouter identifiers for the selected routes.
- Pricing, latency, language quality, speed-control behavior, and authenticated API access remain to be validated. No API requests or paid tests have been performed.

To define together: microphone controls, spoken responses, transcripts, permissions, loading states, and error recovery.

### OpenRouter Integration Review - October 1, 2026

- OpenRouter lists `google/gemini-3.8-flash` for standard text generation, `google/gemini-3.8-flash-lite-tts` for speech generation, and `google/gemini-3.5-transcribe` for completed-audio transcription. [LLM model](https://openrouter.ai/google/gemini-3.8-flash), [TTS model](https://openrouter.ai/google/gemini-3.8-flash-lite-tts), [STT model](https://openrouter.ai/google/gemini-3.5-transcribe).
- Its documented speech endpoints are `/api/v1/audio/speech` and `/api/v1/audio/transcriptions`. The transcription endpoint accepts submitted audio and returns a transcript. The reviewed transcription catalog does not include `google/gemini-3.5-transcribe-live`; live WebSocket transcription through this gateway is not established by the reviewed documentation. This is a compatibility finding, not proof that OpenRouter will never offer it. [Speech generation guide](https://openrouter.ai/docs/guides/overview/multimodal/tts), [Transcription guide](https://openrouter.ai/docs/guides/overview/multimodal/stt), [Current transcription catalog](https://openrouter.ai/api/v1/models?output_modalities=transcription).
- Selected arrangement: use OpenRouter for every AI stage: completed-audio STT in both modes, regular LLM responses, application-scheduled summary/memory LLM calls, and TTS. This supersedes the earlier selection of live STT for continuous conversation.
- Continuous mode remains hands-free: local voice activity detection (VAD) identifies speech and the end of an utterance, then submits its audio for transcription. Transcripts arrive after submission rather than during speech. Use an initial utterance-end silence wait of approximately two seconds after detected user speech stops, confirmed in Step 119. If the user resumes speaking before that interval ends, continue the same utterance and restart the silence wait after speech stops again. Do not submit empty silence as an utterance. This is distinct from proactive follow-up and summary timers and is included in end-to-end response timing. Hold-to-talk still submits on release without adding this wait. Cap captured utterances at 120 seconds under Step 179; at that limit, stop capture and let the user explicitly send the captured speech or record again. VAD library, provider payload support, noise handling, and cap-boundary/runtime tuning require validation.
- Keep the OpenRouter API key on the server and route provider requests through authenticated application endpoints. Direct Google access is outside the selected architecture.
- For Gemini TTS, send expressive delivery instructions through the Google provider's `speech_metadata.style` option, separately from text to be spoken. Verify speaking-speed support: the gateway documents that unsupported models may ignore the speed field or reject non-default values.
- Availability has been checked against public documentation and model listings only. No authenticated or paid requests have been made. Measure Thai-English quality, interruption behavior, latency, and billing before accepting the implementation.

## 5. Production Requirements

### Backend Planning — Current Focus

The owner requested moving discovery to backend design. This changes the current planning focus, not the confirmed product priorities: AI companion first, general assistant next, language tutoring later.

Proposed backend responsibilities, pending technology and model selection:

- Authentication and account identity: Google and email/password sign-in, owner/invitee trial eligibility through an allowed-email list, account access, and recovery. Enforce private-trial authorization in server endpoints as well as page navigation; do not rely on hidden registration controls alone. Only the owner may modify trial eligibility. Database access policies must also enforce trial eligibility so browser access to Supabase cannot bypass the application checks. Revocation preserves data, blocks subsequent protected access, and stops active capture, playback, and unfinished generation across the affected account's surfaces without completing the current reply. Reinstatement restores eligibility but does not automatically resume voice or cancelled work. Validate verified-email handling, registration enforcement, access-state propagation, upstream cancellation, and rejection of late results before implementation.
- Shared persistence: companion profile, settings, conversation messages, summaries, and personalization memory, scoped to the signed-in account.
- Voice orchestration: detect and capture completed utterances, obtain a transcript, generate a response, and deliver expressive speech plus response text. Use OpenRouter for regular STT in both voice modes, LLM, and TTS. Begin speaking when the first completed sentence is ready while the LLM generates the rest, confirmed in Step 121. Submit completed sentences for TTS and play them in order without waiting for the full reply text. Keep captions aligned to actual local playback. Only transient buffers for the current delivery are permitted; release them after playback or cancellation, without keeping an audio replay cache. Sentence-by-sentence delivery is selected product behavior, not yet a verified capability of the chosen routes; validate text streaming, Thai/English sentence segmentation, TTS request behavior, playback continuity, cancellation, and actual provider usage. Do not claim that this alone achieves the three-second response target. Audio delivery transport remains open.
- Text orchestration: accept typed messages and deliver both response text and generated speech without automatically starting microphone listening.
- Personalization: retrieve relevant memory when enabled, combine it with companion settings and current conversation context, and support context-sensitive replies without overwriting saved personality settings.
- Summary and memory processing: summarize conversations and update personalization memory only when memory is enabled; retain memory when message history is deleted.
- User controls: expose history read/resume/delete, memory view/edit/delete/disable, and synchronized settings.

The owner has selected model identifiers for conversation, transcription, and speech generation and selected standard Gemini 3.8 Flash inference for both interactive replies and background summaries/memory updates. OpenRouter serves every AI stage. Both voice modes use completed-audio transcription; continuous conversation detects utterance completion locally, while button mode waits for the user to end the spoken turn. The selected application stack is Next.js, TypeScript, Supabase, and Cloudflare. TTS Thai support, authenticated provider access, deployment configuration, and detailed data design remain to be finalized. No services have been provisioned or application implementation created.

### Selected Technology Stack

- Next.js with TypeScript for the web interface and application API endpoints.
- Supabase Auth for Google and email/password sign-in, with cookie-based server-side session handling. Supabase Postgres stores companion profiles, settings, messages, conversation summaries, and personalization memory. Detailed schema and memory retrieval strategy remain to be designed. [Supabase server-side authentication](https://supabase.com/docs/guides/auth/server-side).
- Cloudflare is the selected hosting platform. Proposed deployment: Cloudflare Workers for the application and API, with static assets for the gallery and interface resources. Cloudflare currently recommends vinext for its Next.js deployment workflow and also documents the OpenNext adapter. Preserve the owner's selected Next.js application structure; validate the deployment path and required features before pinning packages. [Cloudflare Next.js deployment guide](https://developers.cloudflare.com/workers/framework-guides/web-apps/nextjs/), [OpenNext adapter guide](https://developers.cloudflare.com/workers/framework-guides/web-apps/opennext/).
- Proposed background execution: Cloudflare Queues and a consumer Worker for summary/memory jobs, triggered at conversation end or after 15 minutes of inactivity. Retry-safe processing and memory-setting checks must prevent duplicate or late writes. The trigger detection mechanism remains to be defined. [Cloudflare Queues](https://developers.cloudflare.com/queues/).
- OpenRouter handles all AI requests from authenticated server endpoints. Keep its API key and any privileged Supabase credentials in server secrets. Scope user data to the signed-in account and enforce database access policies. Never cache personalized pages, auth responses, or conversation API responses in a shared public cache. [Supabase SSR caching guidance](https://supabase.com/docs/guides/auth/server-side/advanced-guide).

The product architecture is selected; exact package versions, adapter, Supabase region, domain, and deployment configuration remain implementation decisions. Start with free service plans where the deployed application fits their limits; compatibility and resource measurements must establish feasibility. Cloudflare hosting does not imply use of Cloudflare AI models or a replacement for Supabase. No accounts, infrastructure, or paid resources have been provisioned.

Use a custom domain for the private trial, as confirmed in Step 102. The owner's desired domain is `lavenai.space`, which has not yet been purchased. Availability, registration/renewal pricing, registrar, and exact app hostname remain to be verified or finalized. Keep the selected Supabase authentication and allowed-email checks; a custom domain does not make registration public. Cloudflare's supplied `workers.dev` address remains a possible development address, not the selected trial URL. Cloudflare recommends routes/custom domains for production. No domain has been purchased or reserved. Web-address choice does not select an email-sending domain or SMTP provider. [Cloudflare workers.dev documentation](https://developers.cloudflare.com/workers/configuration/routing/workers-dev/).

Service account readiness, confirmed in Step 104: the owner does not yet have Cloudflare, Supabase, or OpenRouter accounts. Account creation, project setup, credentials, funding, and deployment configuration remain setup work. No accounts or projects have been provisioned through this discovery process.

Source-code storage, confirmed in Step 105: keep the project locally and use a private GitHub repository for Git version history and a remote copy. In Step 106, the owner confirmed that they do not yet have a GitHub account; include account creation and private-repository setup in the initial setup plan. No account or repository has been created through this discovery process, no code has been pushed, and deployment automation remains unconfigured. Keep credentials, local environment files, user conversations, memories, and audio payloads out of version control; commit only placeholder variable names in .env.example. This choice preserves Cloudflare hosting and the planned folder structure.

The first private trial has no fixed deadline, confirmed in Step 107. Begin testing when the voice pipeline and core product flows are ready for a usable trial. Prioritize the previously selected voice-quality and conversational-flow validation before inviting testers. This decision does not establish a public launch date.

Initial test surfaces, confirmed in Step 108: an Android phone and web-browser use. The web app remains the base; R001 includes floating delivery in the first release, with Windows selected for floating; Android web support remains unchanged and Android floating is later. Plan real-device microphone, playback, interruption, caption, and session-recovery checks on Android and desktop web. Google Chrome is the primary test browser, confirmed in Step 109. Mobile and desktop retain equal product priority; available test devices and the primary test browser do not establish exclusive platform support or confirm iPhone testing.

### Initial Infrastructure Cost Review - October 1, 2026

- Target Cloudflare Workers Free and Supabase Free for the initial private trial. This is a starting cost target rather than a guarantee that the completed application will fit free-tier limits.
- Workers Free includes 100,000 requests/day and 10 ms CPU per HTTP invocation. Network waiting is excluded from CPU time, but authentication, rendering, and audio/payload processing require profiling. If the application exceeds limits, optimize it or review an upgrade; Workers Paid has a USD 5/month minimum, separate from the AI budget. [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/), [Workers limits](https://developers.cloudflare.com/workers/platform/limits/).
- Cloudflare Queues is available on Workers Free with 10,000 operations/day and 24-hour message retention. Persist job state in Supabase and design retry/recovery so expired queue messages do not silently lose pending work. [Queues free-plan announcement](https://developers.cloudflare.com/changelog/post/2026-02-04-queues-free-plan/).
- Supabase Free includes 500 MB database space, 1 GB file storage, 5 GB egress, and 50,000 monthly active users. Free projects may pause after a week of inactivity. Pro starts at USD 25/month; no upgrade has been selected. [Supabase pricing](https://supabase.com/pricing).
- The built-in Supabase email sender is restricted to project-team addresses and currently two messages/hour. Configure custom SMTP for email verification and password recovery for ordinary invitees. The sending provider, free-tier eligibility, and any domain/email costs remain to be selected; do not add app testers to the Supabase administration team merely to bypass this restriction. [Supabase SMTP documentation](https://supabase.com/docs/guides/auth/auth-smtp).
- The selected USD 10 monthly AI limit covers inference usage. OpenRouter Standard lists a 5.5% credit-purchase platform fee; checkout fees and taxes are outside that inference limit and must be accounted for separately. A USD 10 inference budget is not a guaranteed USD 10 total cash outlay. [OpenRouter pricing](https://openrouter.ai/pricing/).

### Selected Trial Usage Controls

- Enforce a default daily voice allowance of 30 minutes per account and a shared USD 10 monthly AI inference budget for the entire trial. Both controls apply across devices and voice modes; an account cannot reset usage by switching devices or starting another conversation.
- Additionally enforce ten actual web-search calls per account per UTC day across all devices. Search allowance resets at 00:00 UTC (07:00 Thailand). Exhausting it pauses only further searches, subject to the broader voice/conversation access and monthly-budget rules; it does not grant extra voice time or budget.
- Sum elapsed time from every active voice session, including overlapping sessions. Two simultaneous sessions running for one minute consume two minutes of the account's daily allowance. Maintain one account-level usage total with session-level records, and apply exhaustion across all active sessions rather than granting 30 minutes separately to each device or tab.
- The monthly AI budget covers model inference for all accounts, including STT, interactive LLM replies, TTS, summary/memory jobs, and voice previews. This is an internal operating limit, separate from any future subscription price. Hosting, database costs, and funding fees require separate accounting.
- Voice samples played through Settings > My Companion do not deduct daily conversation-time allowance, confirmed in Step 151. Previewing remains available after daily conversation exhaustion if account access and the shared monthly AI budget permit it; this exception does not permit ordinary spoken or typed AI conversation. Keep any local conversation formally paused during previews, with no active-session elapsed-time deductions. Other active surfaces still accrue their own conversation usage. Generating a preview consumes monthly AI budget, and monthly exhaustion or loss of account eligibility must still stop it. Do not apply the preview exception to conversation replies or historical audio; historical replay remains unavailable.
- Count elapsed time from the start to the end of an active voice session against the 30-minute daily allowance, including listening, user speech, thinking/waiting, AI speech, and silent pauses. Apply this to both continuous and button-activated modes; pauses between button-activated turns count while the overall voice session remains active. This replaces the alternative of counting speech duration alone.
- A formally paused session is not an active listening session and does not accrue elapsed-session quota time. In continuous mode, automatically enter this state after two unanswered proactive follow-ups and a further two-minute wait after the second finishes speaking. Require explicit Resume to restart capture and active-time accounting. This differs from ordinary silence while a session remains active. Spoken replies to typed messages while voice listening is paused still follow the out-of-session playback-duration rule.
- Example: 10 seconds of user speech, 30 seconds of AI speech, and 5 seconds of waiting consume 45 seconds of daily allowance. This is a product quota, not a claim that provider audio billing includes all session silence or waiting.
- Spoken replies to typed messages outside a voice session consume the same daily allowance by their actual spoken playback duration. Example: a 30-second spoken reply consumes 30 seconds. A typed reply played during an active voice session is already included in elapsed session time and must not be counted again separately. Both paths also consume the shared monthly AI budget; quota time and provider-billed usage are separate measurements.
- When an account exhausts its daily allowance, pause interactive AI conversation until the daily reset or an eligible owner allowance increase. Do not accept further spoken or typed conversation requests, and do not switch to text-only AI replies. History reading and Settings management remain available. Display a localized quota-reached state with the next reset time.
- Stop that account's current reply generation and speech immediately at daily exhaustion, confirmed in Step 148; do not grant a completion grace period. Apply this across its active surfaces, including spoken typed-message replies outside voice sessions. Stop microphone capture, captions, queued speech, and proactive follow-ups; end active voice-session time accounting without resetting accumulated usage. Discard unsubmitted recordings and transient audio buffers. Preserve already saved text and mark unfinished replies as interrupted. Request upstream cancellation where supported, reject late output from stopped interactive turns, and prevent cancelled retries from restarting them. Resetting or raising the allowance restores eligibility but does not automatically resume microphone listening or replay interrupted replies. Validate shared-account metering, transition timing, and cancellation; stopping does not guarantee that provider charges already incurred can be reversed.
- Daily conversation exhaustion is account-specific, not a suspension of every trial user. Background summary/memory processing remains subject to memory eligibility and the shared monthly budget, separately from the daily conversation allowance.
- Use UTC calendar periods for both usage limits. Reset the per-account daily allowance at 00:00 UTC each day and the shared monthly AI budget at 00:00 UTC on the first day of each month. These resets occur at 07:00 Asia/Bangkok. Apply the same reference timezone across accounts and devices; changing a device clock or timezone must not alter eligibility for a reset. Display the next reset time in a clear localized format.
- When the shared monthly AI budget is exhausted, pause new AI provider calls for all accounts, including conversation STT/LLM/TTS, voice previews, and summary/memory jobs. Keep history reading and Settings available. Retain pending background work in durable job state rather than relying on queue retention until the next month.
- Stop current response generation and speech immediately across all accounts at monthly exhaustion, confirmed in Step 149. Stop microphone capture, queued speech, captions, proactive follow-ups, and active voice-session time accounting; discard unsubmitted recordings and transient playback buffers. Stop any active voice preview. Preserve already saved text and accumulated usage, and mark unfinished replies as interrupted. Request cancellation of in-flight provider work where supported, reject late output from cancelled work, and prevent automatic retries from restarting calls while the budget is exhausted. Keep interrupted eligible background jobs pending for later revalidation rather than marking them successful or losing them. Restoring budget through an eligible owner increase or the next UTC monthly reset does not automatically resume microphones or replay cancelled replies; normal access and daily-allowance checks still apply. Validate shared-budget reservations, spending reconciliation, propagation, and provider cancellation. Cancellation does not reverse already incurred provider charges, and the selected application cap is not yet a verified guarantee against billing overshoot from concurrent or in-flight calls.
- The owner may manually raise the monthly cap in Settings > AI Budget for the current UTC calendar month only. Show current-period spending, the cap, remaining budget, and a control to save a higher current-month cap. Changing the cap must preserve the period's accumulated spending; it must not reset daily allowances or override revoked access or disabled-memory rules. Raising the application cap does not purchase credits or enable automatic provider top-ups.
- At the next monthly reset, expire the temporary increase and restore the USD 10 base cap for the new period. Example: raising the current month's cap to USD 15 leaves the next month's cap at USD 10. Do not carry unused extra allowance into the next month; provider credit balance is separate from the application's monthly allowance.
- After a successful increase leaves sufficient budget, allow eligible new requests and resume eligible pending jobs, rechecking account access, memory state, and deleted-fact exclusions. Underlying provider credits and availability still apply. Store temporary cap changes against the specific UTC month rather than replacing the recurring base cap.
- Navigation to History or Settings does not end the voice session or pause its quota timer. Disconnection pauses the local session until explicit Resume after reconnection. Background continuation and exact session-metering boundaries require runtime validation; ordinary-session closure recovery remains to be defined. Step 136 separately defines restarting unfinished onboarding interviews after closure. The initial monthly AI limit is USD 10, shared across all accounts rather than USD 10 per user. The 15-minute summary inactivity trigger is separate from voice-session metering and does not itself define when an active voice session ends.
- The owner can set a different daily allowance for each account, including the owner's, confirmed in Step 137. The default remains 30 minutes per UTC day; expose individual adjustment in owner-only Settings > Trial Access and enforce it on the server. Changing an allowance preserves accumulated usage across all sessions/devices and does not reset daily spending or bypass monthly budget/access controls. Apply the effective allowance consistently across active sessions; if used time reaches or exceeds a lowered cap, the existing exhaustion behavior applies. Raising the cap can restore eligibility but does not automatically restart a paused microphone. Input bounds and synchronization details remain to be defined. Editing the global default is not selected.
- Individual daily-allowance overrides apply only to the current UTC calendar day, confirmed in Step 138. Return each affected account to the 30-minute default at the next 00:00 UTC reset (07:00 in Thailand), when the ordinary new usage period also begins. Editing an override within the current day preserves that day's used time. Show expiry in the owner interface. Proposed enforcement: bind each override to its UTC date and compute the effective allowance using server time, so an expired value cannot remain effective merely because a cleanup job or client refresh is delayed.
- Show the account's remaining daily allowance through the existing time indicator only, confirmed in Step 139. Do not add five-minute or one-minute advance notices, popups, sound cues, or AI-spoken warnings. Keep normal exhaustion status and reset information when the allowance is reached, alongside the existing pause/enforcement behavior. Use the current server-enforced effective allowance so today's owner override is reflected accurately across surfaces.
- Enforce limits on the server, including background jobs and concurrent requests. Proposed accounting: reserve estimated usage before provider calls, reconcile with measured usage afterward, and expose remaining allowance to the user. Exact metering and reservation rules require implementation validation; do not promise that a post-response cost check alone guarantees an exact spending ceiling.
- Budget management is owner-only and must be authorized on the server, not merely hidden in navigation. Exact layout and other usage presentation remain to be designed within the existing Settings structure.

### Confirmed Logical AI Workflow

#### Interactive conversation path

1. Authenticate the user and load their synchronized companion profile and settings.
   Check trial eligibility, remaining daily allowance, and shared monthly budget before accepting interactive AI work. If the daily allowance is exhausted, expose history and Settings but pause both voice and typed AI conversation until reset.
2. Start microphone listening according to the user's manual/automatic startup setting. Continuous conversation is the default interaction mode; button-activated speaking is also available.
3. In continuous mode, use local VAD to capture an utterance and detect its completion automatically. In button mode, record while the microphone button is held and submit when it is released. Submit completed audio through the application backend to OpenRouter `google/gemini-3.5-transcribe` in either mode. Typed input enters the same response workflow directly.
4. Build the response context from the shared current conversation, configured personality, and relevant personalization memory stored in Supabase Postgres when memory is enabled. Simultaneous sessions contribute to the same context. Proposed orchestration: process accepted turns in a consistent server-defined order to avoid conflicting replies from divergent histories, with unique turn/session IDs to deduplicate retries. Exact synchronization, cancellation, and scheduling mechanisms remain to be designed. The memory retrieval strategy remains open.
5. Generate the reply through standard Gemini 3.8 Flash inference, with streamed text and completed-sentence detection for the selected incremental speech flow, subject to route validation. Allow context-sensitive behavior without modifying saved personality settings. Do not send provider thinking/reasoning content to TTS or display it as the spoken reply.
6. Deliver reply text and send the first completed sentence to the selected Gemini Flash-Lite TTS model without waiting for the whole reply; continue generating and speaking subsequent sentences in order. Use the selected voice, desired speed, and context/personality-appropriate delivery style. Thai support, streaming behavior, exact speech controls, continuity between sentences, and actual costs still require validation. Captions follow audio playback, and the current attempt's temporary audio is discarded after delivery or interruption.
7. Synchronize reply text to the shared conversation, but deliver spoken audio only to the surface that originated the user turn. Show AI captions beneath the circle during local speech and update local listening/thinking/speaking state. Both speakers' messages remain visible across surfaces in the expandable text panel. Typed input also receives audio on its originating surface, even without an active voice session.
8. Persist conversation messages and synchronize them across devices. In continuous mode, local speech detection must stop AI playback and unfinished reply generation as soon as the user interrupts, without waiting for STT. Sending a typed message also stops the originating surface's current AI speech and unfinished reply generation; typing a draft does not interrupt. Capture the new speech turn with normal utterance-end detection or process sent text directly. Clear obsolete playback and prevent late text/audio from the cancelled turn from appending or restarting. Preserve already saved text, mark interrupted replies, and keep independent sessions/turns intact. Use only retained accepted reply text as subsequent context, rather than assuming a cancelled answer completed. Echo cancellation, false interruption prevention, provider cancellation, and interrupted-turn presentation require implementation validation.

#### Background personalization path

1. Use eligible saved conversation text as input for summary and memory-processing jobs when memory is enabled. Exclude messages recorded while memory was disabled, including disabled intervals within a resumed conversation. Re-enabling memory resumes learning from subsequent content only; it does not schedule retrospective processing of the disabled period.
2. Schedule jobs when the conversation ends or reaches 15 minutes of inactivity, and call standard Gemini 3.8 Flash inference through OpenRouter. Do not periodically summarize during active conversation. The exact ending event, activity events that reset the timer, scheduling mechanism, and retry policy remain to be defined. Detect inactivity on the server so that scheduling does not depend on an open browser tab; recheck conversation activity and memory eligibility before processing a queued job. Repeated inactivity checks must not generate another summary for unchanged conversation content.
3. Store one current summary per conversation and extract separate learned fact/preference items into the account's memory store. When an eligible conversation resumes and gains messages, update its existing summary with the additional discussion after the next summary trigger. Reconcile extracted items with existing memories to avoid duplicates. New conflicting information may automatically replace an existing fact/preference value, even one edited manually by the user, without a confirmation step. Enforce deleted-fact exclusions on extraction, summary updates, and writes, including queued jobs already in flight. Only an explicit user instruction to remember the deleted information again can lift its exclusion. Track which messages have been summarized and prevent older jobs from overwriting newer results. Long-conversation processing, uncertain-information criteria, consistency between related summaries and facts, and concurrent-edit handling remain to be designed.
4. Make both summaries and individual fact/preference memories available to subsequent interactive replies when memory is enabled. Select relevant information rather than assuming every stored item must be sent in every prompt, and enforce deleted-fact exclusions so retained summaries cannot bypass deletion. The retrieval and filtering mechanisms remain to be designed. The live response path does not wait for a new summary/memory job to finish.
5. Respect the memory setting during processing: disabling memory stops learning and use of stored memory; handling jobs already in flight and preventing late writes must be designed accordingly. Recheck the current setting and message eligibility before writes. An old job retried after re-enabling must still exclude messages recorded during the disabled period.
6. Deleting message history preserves existing summaries and learned memories. Memory remains separately viewable, editable, and deletable through Settings > Memory.

For shared conversations, evaluate the 15-minute inactivity trigger using activity across all joined sessions rather than an individual tab's idle timer. Stopping one voice session does not by itself end the shared conversation while other sessions continue contributing. Preserve the single-summary rule and prevent duplicate memory jobs for the same conversation revision.

Personalization is currently specified through configured traits, stored memory, and response context. Model fine-tuning has not been requested or selected.

#### Explicit remember command while memory is disabled

1. Recognize the explicit request and identify the specific fact/preference the user wants saved.
2. Present that item and the localized "Enable memory and save this" action. Keep memory disabled while awaiting confirmation; do not enqueue an automatic memory write for the requested item.
3. After the user confirms, authenticate and validate the action, enable memory for the account, and persist the requested item. Prevent duplicate writes from repeated clicks or retries. Report success only after persistence succeeds; define recovery if the setting update or save fails.
4. Resume automatic learning from subsequent eligible content. Do not backfill other messages from the disabled period. If this is an explicit request to remember a previously deleted fact, remove only its corresponding exclusion as part of the confirmed action.

### Owner-Provided Business and Cost Reference — Unverified

- The owner supplied a Voice Tutor Business & Financial Brief as a planning reference. It does not move language tutoring into the first-release scope.
- A future subscription price of USD 15/month is tentative, explicitly not final. The initial release is a private trial for the owner and permitted invitees. The confirmed monthly AI inference budget is USD 10 across all accounts; infrastructure and funding fees are separate.
- The brief assumes approximately 10 seconds of user speech and 30 seconds of AI speech per turn, with approximately 100 response text tokens and 100 response audio tokens. Token counts and billing units require later provider-specific verification.
- The brief lists monthly costs of USD 0.20 for STT, USD 18 for LLM, and USD 0.24 for TTS, while also stating a total AI cost of USD 0.62. These values are inconsistent: the listed components total USD 18.44. A USD 0.18 LLM cost would produce the stated USD 0.62 total, but that correction has not been confirmed by the owner.
- The usage assumption of 15 minutes/day for 20 days equals 300 minutes/month. At 40 seconds per turn, that is 450 turns; 400 such turns equal approximately 266.7 minutes total, including 66.7 minutes of user speech and 200 minutes of AI speech. The intended usage definition remains to be clarified.
- The brief's scaling table uses USD 0.625 AI cost per user for 100, 1,000, and 10,000 users, differing slightly from the stated USD 0.62 unit cost.
- Gross profit, margin, scaling projections, payment fees, hosting estimates, and power-user costs are owner-provided assumptions, not validated economics. They must be recalculated after confirming models, rates, usage, and the intended LLM cost.

Confirmed requirement: account-based synchronization of the companion, settings, conversation history, and memory across mobile and desktop.

### Gemini 3.8 Live Alternative — Comparison Only

After reviewing this comparison, the owner confirmed on October 1, 2026 that the first release will use the original cascaded pipeline: STT -> standard Gemini 3.8 Flash -> TTS. Gemini 3.8 Live remains a reference alternative outside the selected first-release architecture.

| Concern | Selected cascaded workflow | Gemini 3.8 Live alternative |
| --- | --- | --- |
| Voice path | Audio -> STT -> text/context -> standard Flash -> expressive TTS -> audio | Audio/context -> Gemini 3.8 Live -> audio and enabled transcripts |
| Model roles | Separate transcription, reasoning, and speech-generation calls | Native audio conversation model; separate STT/TTS calls are unnecessary for this path |
| Text input | Standard Flash reply, then TTS | Send text into the Live session and receive audio plus its transcript |
| Personality and memory | App builds text context for each response | App supplies personality and relevant memory as session context or through tools; persistent cross-session memory still belongs to the app |
| Caption/history text | Save STT transcript and generated reply text | Enable input/output audio transcription and save the events |
| Interruptions | Coordinate STT, response cancellation, and playback in the app | Built-in Live interruption events; app must stop playback and clear queued audio |
| Speech customization | Dedicated TTS voice/style controls | Validate Live voice selection, tone prompting, and speed control separately; do not assume parity with TTS |
| Background memory | Application-scheduled standard Flash summaries | The same standard Flash summary workflow can remain |

Gemini 3.8 Live is a distinct native-audio model, not the standard Flash model's batch/regular inference toggle. It is designed for low-latency audio interaction. The model-specific page says audio is the response modality and text is obtained through output transcription. It also says the affective-dialog configuration has been removed, so do not copy older affective-dialog examples into this model. [Model documentation](https://ai.google.dev/gemini-api/docs/models/gemini-3.8-live).

Live API documents Thai and English support, transcripts, text input, and interruption handling. Voice-quality and mixed-language behavior still require prototype evaluation. [Live API capabilities](https://ai.google.dev/gemini-api/docs/live-api/capabilities).

#### Alternative cost illustration

Current reference rates per million tokens: audio input USD 3, audio output USD 12, text input USD 0.75, and text output USD 4.50. [Google pricing](https://ai.google.dev/gemini-api/docs/pricing).

At 450 turns with 10 seconds of user speech and 30 seconds of AI speech, 25 audio tokens/second gives USD 0.3375 for newly submitted user audio and USD 4.05 for generated audio: USD 4.3875 for new audio alone. This is not a complete Live bill.

For illustration, add USD 0.675 for 2,000 text-context tokens per turn, approximately USD 0.262 for both transcripts (29.17 user tokens and 100 AI tokens per turn), and USD 0.1125 for the same background summaries. Without accounting for accumulated audio history, this subtotal is approximately USD 5.44. It excludes additional thinking, tool, and infrastructure costs and must not be presented as the cost of a normal persistent session.

Google states that Live re-bills the retained context each turn, including prior user and model audio. Transcripts add output text charges. Context compression affects the amount retained; proactive listening also charges input while listening. [Live billing guidance](https://ai.google.dev/gemini-api/docs/live-api/best-practices).

Worked uncompressed-history example: twenty sessions comprising ten 22-turn sessions and ten 23-turn sessions (450 turns total), submitting only 10 seconds of user audio per turn and retaining 30 seconds of model audio. At turn k, bill 250 new input audio tokens plus 1,000 audio-history tokens for each preceding turn. Summing across sessions gives 4,952,500 billable audio-input tokens, or USD 14.8575. Adding generated audio, the above text-context and transcript assumptions, and summaries gives approximately USD 19.96/month, before thinking and infrastructure. Continuous microphone streaming beyond those ten seconds can raise costs further. Compression or explicit context/session policies can reduce retained-history cost; measure usage metadata to establish a realistic budget.

The selected cascaded estimate is approximately USD 3.72 for 450 turns with regular STT in both modes, bounded average text context, and 200 thinking tokens per reply. The earlier live-STT variant was approximately USD 4.02 under the same assumptions. The Live illustration has different context retention and excludes unknown thinking usage. These are transparent planning scenarios, not measured performance or guaranteed equivalent output quality.

### Calculated AI Cost Estimate — September 30, 2026

This is a planning calculation, not a measured bill. Use paid Google Developer API standard rates as the reference. The chosen routes are OpenRouter for regular STT in both modes, LLM, and TTS. The completed-audio STT column below is the selected baseline; live-STT figures remain comparison scenarios. Gateway funding fees and actual provider usage still need verification before treating this as a complete operating-cost estimate. No batch discount, free-tier allowance, or context-cache discount is assumed. [Google pricing](https://ai.google.dev/gemini-api/docs/pricing), [OpenRouter standard Gemini 3.8 Flash pricing](https://openrouter.ai/google/gemini-3.8-flash).

Reference rates:

| Component | Current rate |
| --- | --- |
| Gemini 3.8 Flash, standard | USD 0.75 / million input tokens; USD 3.75 / million output tokens, including thinking |
| Gemini 3.8 Flash-Lite TTS | USD 0.50 / million text input tokens; USD 6.00 / million audio output tokens |
| Gemini 3.5 Transcribe | Approximately USD 0.005 / minute of user audio, including estimated transcript output |
| Gemini 3.5 Transcribe Live | Approximately USD 0.009 / minute of user audio, including estimated transcript output |

The STT effective rates are Google's approximations; actual transcript token counts vary. TTS uses 25 audio tokens/second: 30 seconds is approximately 750 audio tokens, rather than the 100 audio tokens assumed in the original brief.

STT price comparison rechecked October 1, 2026: completed-audio Transcribe costs USD 2/million audio input tokens and USD 12/million transcript output tokens; Live Transcribe costs USD 3.50 and USD 21 respectively. Both token rates are 1.75 times higher for Live. Google's rounded effective estimates are USD 0.005 versus USD 0.009 per submitted audio minute, approximately 1.8 times higher. At 450 turns with ten submitted seconds each, 75 minutes/month costs approximately USD 0.375 versus USD 0.675, a USD 0.30 difference. One submitted audio hour costs approximately USD 0.30 versus USD 0.54. These amounts include Google's estimated transcript output and exclude the LLM and TTS. If Live receives 300 audio minutes instead of 75, its corresponding approximate STT cost is USD 2.70. Count submitted audio duration rather than treating the entire conversation duration as user speech. The owner initially selected mode-specific STT, then selected completed-audio STT through OpenRouter for both modes in Step 35; the Live figures are retained for comparison only. [Google pricing](https://ai.google.dev/gemini-api/docs/pricing).

Calculation assumptions, not product limits:

- Each turn has 10 seconds of user audio and 30 seconds of AI audio. Only those 10 seconds are submitted to STT in this estimate.
- Each conversational LLM request averages 2,000 uncached input tokens including system instructions, personality, retrieved memory, current message, and conversation context.
- Each reply has 100 visible text tokens plus 200 thinking tokens, making 300 billable LLM output tokens. TTS receives the 100 visible text tokens.
- Twenty background summary/memory calls per month use standard Gemini 3.8 Flash, each with 5,000 input tokens and 500 total billable output tokens.
- Fifteen minutes/day for twenty days is 300 minutes, or 450 forty-second turns. The original 400-turn reference corresponds to approximately 266.7 minutes.

| Cost item | 400 turns/month | 450 turns/month |
| --- | --- | --- |
| STT: completed audio / live | USD 0.33 / 0.60 | USD 0.38 / 0.68 |
| Conversational LLM | USD 1.05 | USD 1.18 |
| TTS | USD 1.82 | USD 2.05 |
| Background summary/memory calls | USD 0.11 | USD 0.11 |
| Total: completed-audio STT / live STT | USD 3.32 / 3.58 | USD 3.72 / 4.02 |

The 450-turn baseline is approximately USD 0.0083–0.0089 per turn, including amortized summary costs. These figures do not substantiate the earlier USD 0.62/month estimate.

Sensitivity at 400 turns: 500 average input tokens and no thinking tokens gives USD 2.57–2.83/month; 10,000 average input tokens and 1,000 thinking tokens gives USD 6.92–7.18/month. These are illustrative workloads, not guarantees or hard bounds. The same voice duration and summary-call assumptions apply.

Google lists doubled standard LLM and selected TTS rates from January 1, 2027. Holding these assumptions and STT rates constant, the selected 450-turn regular-STT baseline becomes approximately USD 7.06/month (USD 7.36 for the earlier live-STT comparison). Recheck rates before launch.

Excluded costs: hosting, database/authentication, storage, audio bandwidth, additional memory retrieval/embedding services, gateway fees, taxes, payment processing, retries, voice previews, and interrupted audio generation. Sending additional audio or silence to streaming STT increases submitted duration; billing must be measured during prototype testing. Longer prompts, additional memory calls, and more thinking tokens also change costs. Selected TTS Thai support still needs resolution; changing TTS may change this estimate.

Confirmed sign-in methods: Google and email/password.

To define together: authentication implementation and account lifecycle, data storage implementation, remaining deletion behavior, privacy, accessibility, exact usage limits and metering, operating costs, deployment, and monitoring.

## 6. Delivery Plan

The deliverable is an online startup MVP, not a local-only prototype. The Director's launch milestones are defined in `outputs/startup-launch-plan.md`; the former local-prototype Executor Brief 01 is superseded and must not be dispatched as the current assignment. The current prepared assignment is `outputs/executor-brief-02-production-foundation.md`; no Executor has been assigned or started. Local tooling and mocked tests may support development, but do not satisfy online release acceptance.

The October 9 task breakdown is in `outputs/task-backlog.md` (82 tasks). `outputs/requirements-coverage.md` maps all 182 discovery decisions and later instructions; `outputs/progress_tracking.md` is the authoritative status/evidence tracker. Use one bounded task per implementation handoff. Coverage mapping does not mean implementation is complete. T069 records the current public GitHub repository versus the earlier private-repository plan without changing repository visibility.

The owner has requested a minimal-budget approach. Keep the existing USD 10/month AI ceiling as a planning control; it is not funded credit or authorization to purchase usage. Identify actual funding, domain, email, hosting, and inference dependencies before promising a launch cost or date. No paid calls or external setup have been authorized by this planning revision.

1. The delivery platform is confirmed as online responsive web. Define the production MVP release gate while retaining the companion-first product and private-trial audience. Public registration remains outside the private trial. R001 includes floating delivery in this first release; Windows is the selected first floating platform; runtime/version evidence is still required.
2. Verify exact OpenRouter identifiers, completed-audio STT, regular streaming LLM replies, expressive TTS, Thai/English quality, speed options, cancellation, and caption alignment. Review replacements under Step 181 and validate the chosen hosting/runtime path before committing implementation effort or paid testing.
3. Assign an Executor to implement the smallest real end-to-end flow: authenticated eligible user, cloud account/settings/history, and a real voice turn through the protected backend. Measure actual cost and latency; do not use simulated replies as evidence that this integration works.
4. Complete selected personalization, onboarding, history, customization, daily/monthly limits, background jobs, cross-session controls, and privacy/deletion guards. Protect provider credentials on the server and verify account isolation.
5. Prepare cloud staging and the actual online private trial. Validate authentication/email delivery, deployment configuration, required domain setup, Android/mobile and desktop behavior, cancellation, recovery, and operating-cost controls. Keep development/staging access distinct from public launch.
6. Launch the limited owner/invitee trial only with real deployed functionality and evidence of readiness. Collect feedback manually, observe actual reliability and spend, and prepare a later public-launch/pricing decision. Deployment, accounts, purchases, and paid testing remain Executor/setup work requiring their own concrete assignments.

### Proposed Low-Budget Implementation Defaults

These are reviewable engineering/design proposals, not new owner-confirmed requirements. They may be adjusted during implementation without another question when doing so preserves the selected behavior and operating budget.

| Detail | Proposed starting point |
| --- | --- |
| Companion autosave | Coalesce typing and keyboard-slider changes after roughly 500 ms of inactivity; commit pointer-slider edits on release. Show Saving/Saved/Could not save; retain failed drafts and guard against older writes overwriting newer edits. |
| Menu/layout | Place the collapsed Menu button at the upper left. Keep the selected desktop side chat panel and mobile bottom chat panel. Use lightweight responsive components within the existing app. |
| History and memory lists | Load about 20 records per page, with a Load more action. Use stable ordering, account scope, and empty states; no new user-facing search service. |
| Input limits | Keep the selected 1,000-character custom-instruction limit. Start with 50 user-perceived characters for companion names and 80 for manually renamed titles; validate Unicode counting consistently. Preserve invalid drafts for correction. |
| Voice samples | Use one short localized sample, approximately five to eight seconds, with the selected saved-personality delivery and saved speed. Preview alone does not change voice selection. Regenerate as needed with transient playback only; no stored audio cache. |
| Gallery | Start with six original or appropriately licensed static assets split between nature/abstract and cute illustrated characters, plus the default lavender circle. Asset creation/licensing remains implementation work. |
| Initial diagnostics | Reuse scoped local development tooling with the developer's own or synthetic test data. No new private-user monitoring dashboard or paid diagnostics service. |
| Caption prototype | If needed, show the currently spoken sentence and clear it at actual completion. Label this as the temporary prototype behavior; retain accurate word-level reveal as the final requirement. |

No paid embedding service, analytics integration, in-app feedback delivery service, or audio archive is added by these proposals. R001 separately records first-release ball/local 2D import and the floating requirement, with runtime/platform choices pending. The first release retains the previously selected features; implementation stages are not a silent reduction of that scope.

First prototype validation priority: voice quality and conversational flow, confirmed in Step 99. Validate Thai, English, and mixed-language transcription and speech output, voice tone, speaking-speed behavior, interruptions, and caption synchronization on mobile and desktop. Personalization/memory behavior and responsive interface usability remain required subsequent validation areas.

Target a normal end-to-end voice response time of no more than three seconds, measured from the user's actual speech completion to the first audible AI response. Include utterance-end detection, STT, LLM, TTS, transport, and local playback startup. Record stage timings to identify delays. This is an owner-selected product target, not verified performance of the selected model routes. Detailed acceptance thresholds and timeout behavior remain to be defined.

Step 119 selects an approximately two-second silence wait in continuous mode, leaving approximately one second for the remaining stages under the three-second target. In Step 120, the owner chose to retain that original three-second end-to-end target rather than revise it to five seconds. Feasibility has not been measured; treat it as an ambitious validation goal. Keep the same measurement start/end points, including silence detection, rather than redefining the metric. Record actual timing and any unmet target during prototype validation.

Plan the initial private trial for one to five participants, including the owner, as confirmed in Step 101. Use this expected total for test planning and shared-budget scenarios. This is not a registration cap or a promise that the USD 10 budget covers every participant's full daily allowance.

R001 updates floating delivery: preserve presence above other applications, the shared companion/session/captions, and hideable controls. Verify the selected Windows floating platform through T078; it ships in the first release and requires T082 acceptance. Android floating and other desktop OS clients remain later. Do not assume universal overlay support or quietly defer it.

## 7. Decision Record

Discovery completion plan: continue asking one question at a time in Thai without a fixed question cap. The current planning estimate is approximately 15-20 remaining main product questions, including Step 54, covering usage/budget, account lifecycle, voice-session behavior, personalization details, failure recovery, and release readiness. This is an estimate rather than a predetermined final count; answers may resolve several decisions or introduce necessary follow-ups. Consolidate the English blueprint as decisions are made. Distinguish owner-confirmed requirements from proposed implementation defaults. Technical compatibility checks are implementation/validation work, not confirmed outcomes of discovery.

Step 1 outcome: Prioritize an AI companion, followed by a general assistant, with language tutoring later.

Step 2 outcome: User-selectable personality, with a Pingo-like persona planned for later exploration.

Step 3 outcome: Hyper-Personalization is the product's core direction. Users select a personality preset and refine traits such as playfulness, gentleness, and response length.

Step 4 outcome: Support automatic learning and explicit memory commands, with user controls to view, edit, delete, or disable memory.

Step 5 outcome: Support continuous conversation and button-activated speaking. Continuous conversation is the default mode.

Step 6 outcome: Launch with Thai and English, automatic language switching, and mixed Thai-English conversation support. Chinese and Japanese are planned for later.

Step 7 outcome: Start with personal use by the owner to test and refine the experience.

Step 8 outcome: Mobile and desktop have equal priority, with a responsive layout suited to each screen size.

Step 9 outcome: Use a voice-focused main screen with a central circle or waveform, microphone control, accessible conversation text, and captions beneath the visualization (described by the owner as "like Pingo").

Step 10 outcome: Show only the AI's response in the captions beneath the visualization while the AI is speaking.

Step 11 outcome: Minimalist styling, lavender purple as the default primary accent, light/dark/system theme options, and user-selectable accent color.

Step 12 outcome: Use a lavender circle with subtle listening, thinking, and speaking animations. Let users customize the image within the circle.

Step 13 outcome: Users select a ready-made circle image from the app's gallery, with the lavender circle as the default before selection.

Step 14 outcome: The full conversation text view shows both user and AI messages and includes a text input and Send button.

Step 15 outcome: Provide one main companion in the first release, with its name, personality, and selected gallery image editable at any time.

Step 16 outcome: Provide a voice library, voice sample previews, and a speaking-speed control. Record the owner's intended TTS model, "Gemini 3.8 Flash TTS," and defer model discussion and technical validation as requested.

Step 17 outcome: Emotional speech tone adapts to both the configured personality and the conversation context.

Step 18 outcome: Automatically save conversation history with read, resume, and delete actions. Summarize each conversation and store the summary in memory for personalization.

Step 19 outcome: Deleting a conversation removes its message history but keeps its summary and learned personalization memory. Memory is managed and deleted separately.

Step 20 outcome: Use one account and synchronize the companion, settings, conversation history, and personalization memory across mobile and desktop.

Step 21 outcome: Support both Google and email/password sign-in.

Step 22 outcome: Users can choose manual session startup or automatic listening when opening the conversation page, subject to microphone permission. Step 59 selects automatic startup as the initial preference.

Step 23 outcome: Thai and English interface languages, initially following the device language and switchable through Settings.

Step 24 outcome: Open the text conversation in the existing voice screen, using a desktop side panel and a mobile bottom sheet, both supporting reading and typing.

Step 25 outcome: Keep Conversation, History, and Settings in the main navigation. Place My Companion and Memory inside Settings, preserving their full controls. Sign In remains the entry screen.

Step 26 outcome: Use a collapsed menu on both mobile and desktop, opened through a Menu button, to keep the conversation screen uncluttered.

Step 27 outcome: AI responses to typed messages are always delivered as both text and speech, independently of voice-session status.

Step 28 outcome: Disabling memory stops both new learning and use of existing personalization memory. Preserve existing memories for later re-enabling, and continue saving conversation history separately.

Step 29 outcome: Let the AI adapt its replies to the conversation context even when this differs from configured traits, while preserving the saved personality settings unchanged.

Step 30 outcome: The owner supplied a tentative future business/cost brief, explicitly left the USD 15 subscription price undecided, and requested moving to backend planning. Step 54 later sets the monthly AI budget; cost and usage inconsistencies in the supplied brief remain recorded for reference.

Step 31 outcome: Select Gemini 3.8 Flash-Lite TTS, Gemini 3.8 Flash, and Gemini 3.5 Transcribe model families. Documentation review identified the need to choose the appropriate serving modes, consider the live STT variant, and resolve Thai coverage for the selected TTS model.

Step 32 outcome: After clarifying inference modes, the owner selected regular Gemini 3.8 Flash. Use standard inference for both interactive replies and application-scheduled background summaries/memory updates. The provider Batch API is outside the selected scope. Record the complete logical conversation and personalization workflow.

Architecture comparison outcome (October 1, 2026): Retain the original STT -> standard Gemini 3.8 Flash -> TTS pipeline after comparing it with Gemini 3.8 Live.

Step 33 historical outcome: Initially select `gemini-3.5-transcribe-live` for continuous conversation and `gemini-3.5-transcribe` for button-activated speaking. Superseded by Step 35.

Step 34 outcome: Select OpenRouter as the preferred API gateway. Public listings confirm the selected regular LLM, TTS, and completed-audio STT, but do not establish support for the selected live STT model.

Step 35 outcome: Use OpenRouter for every AI stage. Both voice modes use `google/gemini-3.5-transcribe` after each utterance ends. Continuous mode detects utterance completion locally and remains hands-free. This replaces the earlier live-STT selection. The LLM, TTS, and background LLM calls also use OpenRouter.

Step 36 outcome: Select Next.js, TypeScript, and Supabase for accounts and application data, with Cloudflare as the hosting platform. Record the planned folder structure. Workers deployment and Queues-based background processing are the proposed implementation arrangement, subject to compatibility validation and scheduling decisions.

Step 37 outcome: Generate summaries and automatic personalization updates when the conversation ends or after inactivity. Run this in the background only when memory is enabled, without periodic summarization during active conversation. Step 38 defines the inactivity threshold.

Step 38 outcome: Select 15 minutes of inactivity before scheduling a conversation summary. This does not prevent resuming saved conversations and is independent of STT utterance-end detection.

Step 39 outcome: Maintain one current summary per conversation. When the user resumes it and adds discussion, update the existing summary at the next eligible end/inactivity trigger instead of storing separate summaries for each resumed segment.

Step 40 outcome: Store conversation summaries plus separate learned fact/preference items. Users can view, edit, and delete each individual item through Settings > Memory. Both forms are account-scoped and stored in Supabase Postgres.

Step 41 outcome: Restore a deleted fact/preference only after an explicit user instruction to remember it again. Do not automatically relearn it from history, retained summaries, or new conversations. Apply the rule across both memory forms and pending background jobs.

Step 42 outcome: After memory is re-enabled, learn only from subsequent conversation content. Do not process the memory-disabled period retrospectively. Keep its history readable and apply this eligibility boundary even within a resumed conversation.

Step 43 outcome: Offer an "Enable memory and save this" button when the user explicitly asks to remember something while memory is disabled. Wait for confirmation before enabling memory and saving that specific item. Do not learn retrospectively from other disabled-period messages.

Step 44 outcome: Allow automatic updates when newly learned information conflicts with existing fact/preference memory, including items the user edited manually. Do not require confirmation for those replacements. Preserve the existing restrictions on disabled memory, deleted facts, and saved companion settings.

Step 45 outcome: Do not notify users about automatic memory creation or updates. Keep resulting memory visible and manageable in Settings > Memory. Preserve the confirmed explicit-save confirmation when memory is disabled.

Step 46 outcome: Select an invite-only trial for the owner and explicitly permitted invitees. Do not enable public registration as part of the initial release. Keep each account's data independent.

Step 47 outcome: Use an allowed-email list. The owner adds permitted email addresses, and their owners can access the trial after authentication through Google or email/password. Store eligibility in Supabase and enforce it using verified account identity.

Step 48 outcome: Manage the allowed-email list in Settings > Trial Access, accessible only to the owner. Provide view, add-email, and revoke-access actions. Protect the page and mutation endpoints with server-enforced owner authorization.

Step 49 outcome: Revoking trial access preserves the invitee's account data while blocking application access. Reinstating the same account restores access to its companion, settings, history, and memory. Provide a Reinstate access action in the owner-only section.

Step 50 outcome: Enforce both a daily voice allowance per account and a shared monthly AI budget for the trial. Exact limits, metering, resets, and exhaustion behavior remain to be defined.

Step 51 outcome: Set the default daily voice allowance to 30 minutes per account, shared across that account's devices, voice modes, and conversations. Step 52 defines how active voice sessions consume it.

Step 52 outcome: Count elapsed voice-session time, including silence, pauses, and waiting, from session start to session end. Do not count speech duration alone. Avoid double-counting typed-message audio played inside an active voice session.

Step 53 outcome: Deduct spoken playback time from the daily allowance for typed-message replies outside an active voice session. A 30-second spoken reply uses 30 seconds. Do not double-count replies played inside an active voice session.

Step 54 outcome: Set the shared monthly AI inference budget to USD 10 for all trial accounts combined. Target Cloudflare and Supabase free plans initially, subject to runtime and resource validation. Record free-tier limits and the separate email-delivery/funding costs.

Step 55 outcome: Pause both voice and typed AI conversation when the daily allowance is exhausted, until reset. Keep history reading and Settings management available; do not provide a text-only conversation exception.

Step 56 outcome: Use UTC as the common reset timezone. Reset daily allowances at 00:00 UTC and the shared monthly AI budget on the first day of the month at 00:00 UTC, equivalent to 07:00 Asia/Bangkok. Use server-derived periods consistently across accounts and devices.

Step 57 outcome: Pause all AI calls at shared monthly budget exhaustion, but allow the owner to raise the cap manually in Settings. Preserve spending already recorded and resume only when budget is available. Do not automatically raise the cap or purchase provider credits.

Step 58 outcome: An owner-raised cap applies only to the current UTC calendar month. At the next monthly reset, restore the USD 10 base cap. Preserve current spending when raising the cap and keep provider credits separate from monthly allowance.

Step 59 outcome: Default to automatic listening on entry to the Conversation page after microphone permission is granted and account/usage checks pass. Begin daily quota timing when the session actually starts. Retain the manual-start option in Settings and honor explicit Stop actions.

Step 60 outcome: Continue an active voice session across in-app navigation to History and Settings, with compact persistent controls. Continue elapsed-session quota accounting and reuse the same session when returning to Conversation.

Step 61 outcome: Allow simultaneous voice sessions for the same account across devices and browser tabs. Keep each session's audio and lifecycle independent, and add all session durations together against the shared daily allowance. A new session does not stop an existing one.

Step 62 outcome: Simultaneous sessions for the same account use one shared conversation, synchronized messages, and shared response context. Preserve independent session audio/lifecycle controls and summed quota accounting. Maintain one conversation history and current summary.

Step 63 outcome: Play each AI reply's audio only on the originating device/tab. Synchronize text to the shared conversation across surfaces without broadcasting speech. Apply this to both spoken and typed input, with captions and speaking-state animation tied to local playback.

Step 64 outcome: Use hold-to-talk in button-activated mode: hold to record, release to stop and submit the spoken turn. Keep overall session termination separate, and continue counting elapsed session time between turns.

Step 65 outcome: Sending a typed message interrupts the current local AI speech and starts processing the new message without waiting for speech completion. Typing without sending does not interrupt. Clear obsolete local audio while preserving shared history and other sessions.

Step 66 outcome: If speech generation or playback fails, display available reply text with a manual "Retry audio" action. Originally allowed reuse of generated audio when possible; the revised Step 110 no-storage policy now requires fresh TTS for the manual recovery action on the current failed reply. Do not rerun the LLM or duplicate messages. Respect existing access and usage limits. This recovery action does not provide voice replay of historical messages.

Step 67 outcome: Reveal whole words progressively during speech. Accumulate the current sentence, clear it at its spoken completion, then start the next sentence. Clear the final caption when speech ends; keep the full reply in chat. The initially requested single-line layout is refined by Step 68 below. Exact speech alignment requires validation.

Step 68 outcome: Start captions on one row and wrap to additional rows when the sentence fills the available width. Keep revealing words and retaining the current sentence until it finishes being spoken, then clear all its rows before the next sentence. This supersedes strict single-line captions and horizontal scrolling.

Step 69 outcome: Use all four initial personality presets: Warm and gentle, Playful and talkative, Calm and attentive, and Friendly and direct. Each remains adjustable through personality traits.

Step 70 outcome: New accounts start with Warm and gentle, without a required personality-selection step before the first conversation. Users can change the preset and adjust personality traits later in Settings > My Companion.

Step 71 outcome: Use sliders for adjustment of personality traits, including playfulness, gentleness, and response length. Step 159 subsequently selects five discrete levels. Step 160 subsequently selects new-account initial values; detailed response-length guidance remains to be defined.

Step 72 outcome: Preserve the current saved trait slider values when switching personality presets. Change the selected preset while retaining the user's trait adjustments.

Step 73 outcome: Allow the AI to initiate a conversational follow-up after a period of user silence during an active continuous voice session. Step 74 selects a 30-second wait and Step 75 limits unanswered follow-ups to two. Concurrent-session coordination remains to be defined separately from utterance-end detection and the 15-minute summary timeout.

Step 74 outcome: Wait 30 seconds after local AI speech finishes, with no new user speech or sent message, before initiating a proactive follow-up in an eligible active continuous session. Do not trigger while user input, reply generation, or playback is in progress.

Step 75 outcome: If the user does not answer, allow one additional proactive follow-up after another 30 seconds of silence following the first follow-up's speech. Make at most two unanswered proactive follow-ups total. Step 77 adds automatic pause after a further two-minute wait; active-time accounting continues until that pause takes effect.

Step 76 outcome: Enable automatic conversation follow-ups by default and allow users to turn them off or on in Settings. Synchronize this preference across the account's devices.

Step 77 outcome: After the second unanswered proactive follow-up finishes speaking, wait a further two minutes without user input, then automatically pause the local session's microphone listening and elapsed-session quota accounting. Require an explicit Resume conversation action. Preserve the conversation and keep the 15-minute summary inactivity rule separate.

Step 78 outcome: Attempt to continue the existing local voice session when the user switches tabs/apps or locks the screen, where the browser and device support it. Fall back to a paused state when continuation is unavailable. Runtime validation remains required. The owner additionally requests an interactive floating companion with a customizable picture; Document PiP is the proposed desktop route, with an in-page fallback for unsupported browsers.

Step 79 outcome: Include the companion picture, session status, captions, and pause/resume and stop controls, with a control menu that users can hide and reveal. Defer the floating companion to a future desktop software phase rather than requiring it in the first browser release. No desktop framework or browser PiP implementation has been selected for delivery.

Step 80 outcome: Keep the user's transcribed text in conversation history without persistently storing the user's recordings or offering playback of those recordings. Temporary audio processing and provider-side data handling require implementation review. Generated AI audio retention is a separate decision.

Step 81 outcome (superseded by the revised Step 110 decision): Initially selected temporary caching for generated AI audio and TTS regeneration when unavailable. The owner subsequently requested no audio storage at all. The current requirement is no reusable audio cache. Step 112 additionally removed Listen again from historical messages; History is text-only.

Step 82 outcome: Automatically delete message history after seven days, replacing the proposed 90-day period. Preserve existing personalization summaries and fact/preference memories under the separate memory-management rules. Step 83 defines the conversation-level retention clock.

Step 83 outcome: Expire the conversation's message history after seven days without a new spoken or typed user turn in that conversation. Returning to chat restarts the clock for the conversation. Viewing history, background processing, and proactive AI messages alone do not extend retention.

Step 84 outcome: Allow users to delete their own account and personal app data from Settings after explicit confirmation. Delete the companion profile, settings, history, summaries, personalization memories, deletion exclusions, and any associated transient audio buffers (audio caching was superseded by the revised Step 110 decision). Account deletion is separate from history deletion and trial-access revocation. Cleanup implementation and deletion timing still require definition.

Step 85 outcome: Wait seven days after confirmed account-deletion requests before permanently deleting the account and personal app data. Provide explicit cancellation during that period and show the deletion deadline. Keep this waiting period separate from seven-day conversation-history retention.

Step 86 outcome: Restrict a pending-deletion account to deletion status and explicit cancellation during the seven-day wait. Stop its voice sessions and pause AI conversation and memory learning. Signing in alone does not cancel deletion. Normal app access resumes only after cancellation and the existing eligibility/usage checks.

Step 87 outcome: After permanent account deletion, require the owner to authorize the email again before a fresh account can access the private trial. Prior invitation eligibility does not carry over automatically. Reauthorization does not restore deleted personal data.

Step 88 outcome: Start a new conversation by default when a new voice session begins after all previous sessions have ended. Keep old conversations available for explicit resumption through History until expiry. Preserve companion settings and eligible personalization memory. Joining an already active shared conversation or explicitly resuming a paused session retains the existing conversation behavior.

Step 89 outcome: Switching to another conversation or resuming a different history thread moves every active session for the account to that same shared conversation. Preserve the prior history and continuous session-time accounting. Do not introduce separate active threads or broadcast new reply audio to other surfaces.

Step 90 outcome: Give a short AI greeting first when a new conversation starts, following the configured personality, then let the user speak. Keep normal text-plus-speech behavior and generate one greeting for the shared conversation rather than duplicating it for joining surfaces.

Step 91 outcome: Personalize the opening greeting with relevant eligible saved preferences or interests when memory is enabled. Respect deleted-fact exclusions and use a general personality-based greeting when memory is disabled or no suitable memory is available.

Step 92 outcome: Include web search in the first release using Parallel Fast through OpenRouter, with an account-synchronized Web search on/off toggle in Settings. Keep search within the existing shared monthly AI budget. Step 93 selects off as the default. Source presentation and exact call limits remain to be defined; Thai result quality and integration compatibility require validation.

Step 93 outcome: Web search is off by default for new accounts. Users can enable it explicitly in Settings; synchronize the preference and enforce it for provider calls.

Step 94 outcome: Display clickable source links only in the chat panel, attached to the relevant web-assisted AI reply. Do not automatically read source names, URLs, or citation markers aloud; captions follow the speakable reply.

Step 95 outcome: Limit web search to ten actual search calls per account per UTC day, shared across devices, with reset at 00:00 UTC (07:00 Thailand). At exhaustion, block new searches while permitting conversation without new web searches when the other access and usage limits allow it.

Step 96 outcome: Retry recoverable transcription or text-reply generation failures automatically once, then show a manual Retry action if still unsuccessful. Retry the failed stage for the existing turn, recheck access/usage, and avoid duplicate saved messages. Preserve the manual Retry audio behavior for TTS/playback failures.

Step 97 outcome: Pause microphone listening and elapsed-session quota accounting when connectivity is lost. After reconnection, remain paused until the user explicitly selects Resume conversation and eligibility checks pass. Preserve the saved conversation and prevent automatic microphone restart or duplicate opening greetings.

Step 98 outcome: The app's product name is Laven AI. Keep this separate from the individually customizable companion name.

Step 99 outcome: Validate voice quality and conversational flow first, including Thai/English speech, interruptions, and response timing. Continue to validate personality/memory behavior and responsive interface usability afterward; all confirmed first-release requirements remain in scope.

Step 100 outcome: Target first audible AI speech within three seconds after the user finishes speaking under normal conditions, including utterance-end detection and the full selected STT/LLM/TTS pipeline. Verify through prototype measurement; no provider performance guarantee is established.

Step 101 outcome: Plan for one to five participants in the initial private trial, including the owner. Use this as a test-planning and budget-scenario assumption, not a hard account limit.

Step 102 outcome: Use a custom domain for the private trial of Laven AI. Exact domain and ownership status are pending; this selection does not purchase or reserve a domain or select an email provider.

Step 103 outcome: The desired domain is lavenai.space. The owner has not purchased it yet. Availability, registrar, registration and renewal prices, and DNS/hosting configuration remain unverified.

Step 104 outcome: The owner does not yet have accounts for Cloudflare, Supabase, or OpenRouter. Include creation and configuration of all three in the setup plan. No account, project, or credential configuration has been completed.

Step 105 outcome: Keep the project locally and in a private GitHub repository, with Git version history and a remote copy. No repository has been created or pushed. GitHub account readiness and deployment automation remain separate setup details.

Step 106 outcome: The owner does not yet have a GitHub account. Include GitHub account creation and private-repository setup in the initial setup plan. No account or repository has been created through this discovery process.

Step 107 outcome: No fixed deadline for the first usable private trial. Begin testing based on readiness of voice quality and core product flows, rather than a calendar commitment. A public launch date is not selected.

Step 108 outcome: The owner will test using Android and a web browser. Keep the first release browser-based and plan Android and desktop-web validation. The primary browser remains to be identified, and iPhone test-device availability is not confirmed.

Step 109 outcome: Google Chrome is the owner's primary test browser for the selected Android and web-browser test surfaces. Record actual device and browser versions during validation; this choice does not restrict the product to Chrome.

Step 110 revised outcome: Do not store generated AI audio for reuse, replacing the temporary-cache choice. Allow only transient processing/playback buffers, discarded after the attempt ends. At this step, Listen again and manual Retry audio were to generate TTS from saved reply text under existing usage and budget controls. Step 112 subsequently removed history replay; only current-reply speech-failure recovery remains. No LLM rerun or duplicate chat message is needed. Seven-day text-history retention is unchanged.

Step 111 outcome: The owner requested keeping only text. Retain conversational text without audio files, a reusable audio cache, or original per-reply voice/speed/style snapshots. The replay policy selected at this step was superseded in Step 112 when the owner removed history voice replay. This media-retention decision preserves the selected account-level settings, personalization memory, source links, and seven-day text-history policy.

Step 112 outcome: Default to short, concise replies, roughly one to three sentences. Keep the user-adjustable response-length slider and context adaptation. The owner also removed voice replay from historical chat: History is text-only, with no Listen again or old-message speech-regeneration controls. New replies retain text and speech, and manual Retry audio remains available for the current failed speech attempt. This supersedes the earlier history-replay feature and its voice-setting policy.

Step 113 outcome: Use short topic-based conversation titles with dates in History. Title-generation timing, budget checks, and a temporary date/time fallback remain implementation details to define. History stays text-only without voice replay.

Step 114 outcome: When switching between continuous conversation and hold-to-talk during local AI speech, stop that speech and change mode immediately. Clear obsolete playback and captions, reject late audio for that speech attempt, and preserve saved text, shared conversation, the existing session, and quota accounting. Other sessions remain independent.

Step 115 outcome: Offer both flowers/nature/minimal abstract images and cute illustrated characters/animals in the companion-image gallery. Keep the default lavender circle and gallery-based customization. This choice does not add personal uploads, animated character personas, or the future desktop floating companion. Exact assets and collection size remain to be defined.

Step 116 outcome: Include an optional free-text field for additional personality/conversation-style instructions in Settings > My Companion, alongside presets and sliders. Users can edit or clear it, and it is synchronized as an account-level companion setting. It is optional and initially empty. Step 172 subsequently selects a 1,000-character limit with a counter; Step 117 gives custom text precedence when style settings conflict, and Step 158 selects Settings autosave.

Step 117 outcome: Give user-written custom personality instructions precedence over conflicting preset/slider style preferences. Continue applying presets and sliders where custom text does not conflict. Do not automatically rewrite saved settings, and retain context adaptation and server-enforced access, memory, search, and usage rules.

Step 118 outcome: Include Add memory in Settings > Memory for directly entering and saving a fact/preference. Keep automatic learning and conversational remember requests. Treat deliberate direct saving as an explicit remember action for that item, including item-specific restoration of a deleted fact. When memory is disabled, require the existing Enable memory and save this confirmation before enabling and saving. Preserve account isolation, synchronization, editing/deletion, and the existing automatic conflict-update policy.

Step 119 outcome: Wait approximately two seconds after detected user speech stops before submitting the utterance for transcription in continuous mode. Resume capture if speech continues before the interval ends, and restart the wait after the next pause. This is an initial threshold for real-device validation, not a provider latency guarantee. Hold-to-talk submission on release, the 30-second proactive-follow-up timer, and the 15-minute summary timer remain separate.

Step 120 outcome: Retain the original three-second target from actual user speech completion to first audible AI speech, including the approximately two-second utterance-end silence wait. Do not switch to a five-second target. This remains an ambitious goal requiring prototype measurement rather than a verified provider-performance or delivery guarantee.

Step 121 outcome: Begin speaking when the first completed sentence is ready while the remaining reply is generated. Continue sentence-by-sentence in order. Keep text-and-speech delivery, AI-only playback-aligned captions, interruption rules, and no audio storage for reuse. Validate route capabilities, sentence segmentation, playback continuity, and actual costs; the three-second response target remains unverified.

Step 122 outcome: Speaking over the AI or sending a new message stops both local speech and unfinished generation of the old reply. Preserve already saved text, mark the reply as interrupted, clear obsolete audio/captions, and reject late output from that cancelled turn. Capture a new spoken turn immediately but retain the normal two-second end-of-utterance wait; process sent text directly. Other independent turns/sessions remain intact. A voice-mode change alone follows Step 114 rather than this new-turn rule.

Step 123 outcome: In an active continuous session, pressing the microphone control mutes only microphone input. AI generation/speech for accepted turns can continue, typed messages remain available, and elapsed-session quota keeps running. Unmute returns microphone input within the same session without resetting quota or adding a greeting. Keep the explicit Stop session control and independent behavior of other sessions. Hold-to-talk control behavior is unchanged.

Step 124 outcome: Continue automatic silence-triggered AI follow-ups while the microphone is manually muted, subject to the saved follow-up toggle and normal access/usage controls. Retain 30-second waits, at most two unanswered follow-ups, and automatic local pause two minutes after the second finishes without new input. Do not automatically unmute. Elapsed-session quota continues while active and stops only when the session pauses or ends. Typed input retains its normal effect on the follow-up sequence.

Step 125 outcome: Correct transcription errors by sending an ordinary new typed message, such as clarifying what the user meant. Do not add a message-editing or answer-regeneration flow for the first release. Preserve the original history and apply the existing typed-message, interruption, synchronization, memory-eligibility, and usage rules to the correction.

Step 126 outcome: Show a brief optional companion-setup screen after first eligible sign-in, offering personality, gallery image, and voice choices with a Skip action. Continue saves the chosen settings and opens Conversation; Skip uses saved/default settings. Preserve the ability to start without choosing a preset and later customization through Settings > My Companion. Account-level setup completion is the proposed cross-device implementation.

Step 127 outcome: Include optional user-introduction questions at the beginning of first eligible sign-in/use, alongside companion setup. Initially described as an onboarding quiz; Step 129 replaces its form-style presentation with an AI-led interview. Gather nickname, interests, and conversation preferences; allow skipping. Explicitly saved introductory facts/preferences use the existing manageable-memory and disabled-memory confirmation rules. Keep account-level companion settings separate. Onboarding is planned, not implemented.

Step 128 outcome: Use approximately three to five introduction questions. Keep onboarding optional and skippable, and allow personalization to grow through subsequent eligible conversation and direct memory entry. Step 129 preserves this length while changing the format to an AI-led interview. Exact prompts and final count within that range remain to be defined.

Step 129 outcome: The owner proposed having the AI interview new users instead of using a form-style quiz. Select an optional AI-led conversational introduction: one friendly question at a time, adapting subsequent questions to answers, within approximately three to five questions. Use the existing LLM and access/usage controls. Voice versus text-only interview delivery remains to be selected in Step 130.

Step 130 outcome: Use voice as the primary onboarding-interview channel, with readable text and typed-answer fallback. Use the selected STT/LLM/TTS pipeline, continuous-voice defaults, explicit Start interview/microphone permission, and existing access, daily-allowance, monthly-budget, and interruption controls. Interview voice time counts toward the existing shared allowance. Do not retain generated audio for replay.

Step 131 outcome: The owner requested revised interview topics and asked for three variants. Propose an enjoyable-interests introduction, a comfort/connection introduction, and an everyday-life introduction, each illustrated with four adaptive question topics. No variant is selected yet. Preserve voice-first delivery, typed fallback, optional participation, and the approximate three-to-five-question range.

Step 132 outcome: Select Variant 1, Start with enjoyable things, supplemented with preferred name/nickname, interests/hobbies, expectations of an AI companion, and conversation-style preferences. The owner also requested target-language, self-reported familiarity, and learning-purpose questions. The friendly AI interview remains adaptive and optional; do not repeat already covered topics. Step 133 subsequently includes the learning questions as an optional onboarding branch, expanding the full interview to approximately six to eight questions when all are asked. Language-tutor delivery remains in the previously selected later phase.

Step 133 outcome: Include the three language-learning questions during initial onboarding as an optional branch. Ask the target language, self-reported familiarity, and learning purpose; skip remaining learning questions if the user is not interested or has no target language. Avoid asking for information already provided. With all core and learning questions, the total is approximately six to eight. Language-tutor delivery remains a later feature.

Step 134 outcome: Save eligible onboarding facts/preferences automatically after interview completion, without an ordinary pre-save review screen. Users can view, edit, and delete them later in Settings > Memory. Preserve disabled-memory eligibility and explicit-save confirmation, deleted-fact exclusions, normal access/usage limits, and separately saved companion settings. Saving is subject to successful processing/persistence, with existing durable pending-job handling where needed.

Step 135 outcome: End the completed onboarding interview and start a new normal conversation. Keep the interview transcript as a separate text-only History entry with the existing seven-day retention. Preserve accumulated usage, saved companion settings, and memory eligibility. Apply ordinary session-start, shared-thread switching, and greeting rules after rechecking access/usage. Personalization uses successfully saved eligible memory rather than claiming pending onboarding facts were already stored.

Step 136 outcome: Start a new interview on the next visit if the app closed before completion. Do not resume prior interview progress. Preserve saved companion settings, existing memory, and used quota; allow skipping. Keep the abandoned interview's accepted text under normal seven-day history retention, without automatically saving its onboarding facts. Reject late jobs/output from the abandoned interview. Temporary network interruption within an open app still follows the existing pause/explicit-Resume rule.

Step 137 outcome: Allow owner-only adjustment of each trial account's daily allowance, including the owner's account, in Settings > Trial Access. Keep 30 minutes as the default. Preserve accumulated usage, UTC resets, account-shared metering across devices, and the separate shared USD 10 monthly AI budget. Server authorization must prevent ordinary users from changing their allowance. Step 138 subsequently limits each override to the current UTC day.

Step 138 outcome: Apply each owner-set individual allowance override only to the current UTC day. At the next 00:00 UTC reset (07:00 in Thailand), return to the 30-minute daily default and begin the ordinary new usage period. Saving or editing an override during the current day does not erase used time. Enforce expiry using server-side UTC-date checks and show it in the owner interface.

Step 139 outcome: Display only the existing remaining-time indicator, without additional five-minute/one-minute advance notices, popups, sounds, or AI-spoken warnings. Preserve quota enforcement and the normal exhausted-state/reset information. Reflect the account's current effective allowance, including a valid owner-set override.

Step 140 outcome: Interview first using saved/default companion settings, then offer optional personality, gallery image, and voice customization. End interview voice-session accounting before customization. After chosen settings are saved or customization is skipped, start a new normal conversation under the existing startup, greeting, usage, and synchronization rules. Keep onboarding optional and preserve user control of saved settings.

Step 141 (confirmed): Recommend a personality preset, gallery image, and voice after the interview using the user's interview answers. The user confirms suggested choices or selects alternatives before saving. Suggestions must use real available catalog entries, preserve unrelated settings and saved trait sliders, and respect access and AI-budget controls. Memory-off interviews may inform transient suggestions but must not create hidden saved memory. Recommendation-generation details and cost require validation.

Step 142 (confirmed): Stop active conversations immediately when the owner revokes account access, including microphone capture, speech playback, captions, and unfinished generation on all of that account's active surfaces. Do not complete the current reply; block subsequent protected requests and late response/memory writes. Preserve already saved account data and accumulated usage, stop active session-time accounting, and discard transient audio. Request provider cancellation where supported, with stale-result rejection regardless of cancellation support. Reinstatement requires explicit user action to resume voice. Access propagation and cancellation remain to be validated; no zero-delay guarantee is made.

Step 143 (confirmed): Discard the unfinished utterance when the user mutes during speech before its audio has been submitted for transcription. Release transient recording buffers and cancel any pending utterance-end submission timer; do not call STT or create a message/reply from the discarded recording. Unmute starts fresh capture in the same session. Already submitted turns, typed input, proactive follow-ups, and elapsed-session quota retain their existing behavior. Capture/submission race handling requires validation.

Step 144 (confirmed): Discard the unsubmitted utterance and switch voice modes immediately when the user changes modes during local recording. Release transient audio, cancel pending submission timers, and reject stale capture or hold-release events. Do not submit that audio to STT or create a turn from it. Preserve the current conversation, session, mute/pause state, and usage accounting. Fresh capture follows the new mode's controls and normal eligibility checks; hold-to-talk requires a fresh press. Switching after submission is resolved in Step 145.

Step 145 (confirmed): Switch input mode immediately while allowing an already submitted turn to finish transcription, reply generation, and normal text-and-speech delivery when the change occurs before AI playback starts. Do not cancel or restart that turn merely for a mode change. Preserve local audio routing, session/conversation state, and usage accounting; subsequent input follows the new mode. Switching during playback follows Step 114, and new spoken/sent input follows Step 122. Normal eligibility, interruption, and stopping controls still apply. Validate ordering at the processing-to-playback boundary.

Step 146 (confirmed): Use Laven as the initial companion name for new accounts, editable in Settings > My Companion. Preserve the spelling across Thai and English interfaces, and retain any saved custom name across sign-ins and onboarding recommendations. The product name remains Laven AI. No required naming step is added.

Step 147 (confirmed): Use English as the initial interface fallback when the device language is neither Thai nor English and no user preference exists. Supported Thai/English device locales select the matching interface, while a saved choice takes precedence across devices. Keep language switching in Settings and conversation-language detection independent of interface language.

Step 148 (confirmed): Stop current reply generation and speech immediately when the account's daily allowance is exhausted, without a completion grace period. Stop microphone capture, captions, queued speech, and proactive follow-ups across that account's surfaces, including out-of-session typed-reply playback. Preserve saved text and accumulated usage, mark unfinished replies as interrupted, release transient audio, and reject late interactive output. Request provider cancellation where supported. New voice/typed AI requests remain blocked until reset or an eligible owner allowance increase; History and Settings remain readable. Restored eligibility does not automatically resume the microphone or interrupted replies. Background summary/memory eligibility and the shared monthly budget remain separate. Metering/cancellation validation is required, and already incurred provider costs may remain payable.

Step 149 (confirmed): Stop current response generation and speech immediately for all accounts when the shared monthly AI budget is exhausted. Stop active capture, playback, captions, previews, and proactive follow-ups without a completion grace period. Preserve saved text and usage; mark unfinished replies interrupted. Request in-flight provider cancellation where supported and reject cancelled work's late output. Block new calls and retries, retaining eligible unfinished background jobs in durable pending state for revalidation when budget returns. History and Settings remain available. Budget restoration does not automatically resume microphones or replay interrupted replies. Provider charges already incurred may remain payable; reservations, reconciliation, cancellation, and cross-account propagation require validation.

Step 150 (confirmed): Selecting a voice preview in Settings pauses the active local voice conversation before sample playback. Stop capture and conversational audio/captions, suspend local active-session time accounting, and prevent preview feedback or stale conversational audio. Preserve the conversation and usage; other surfaces stay independent. Remain paused when the preview ends, is cancelled, or fails, and require explicit Resume with normal eligibility checks. Do not automatically restart the microphone or replay interrupted conversation audio. Shared AI-budget checks and transient-only preview audio still apply. Step 151 excludes preview playback from daily deductions; Step 152 cancels unfinished local accepted work when the preview starts.

Step 151 (confirmed): Do not deduct Settings voice-sample playback from the daily conversation-time allowance. Preview generation still consumes the shared monthly AI budget. Allow previews when daily conversation allowance is exhausted, subject to account eligibility and available monthly budget. Keep the local conversation paused with no elapsed-session deductions while other active surfaces continue their own metering. The preview exception does not enable ordinary conversation or historical replay, and Resume still requires available daily allowance.

Step 152 (confirmed): Starting a voice preview cancels unfinished processing of the local accepted turn, including STT or reply generation, while preserving text already saved. Mark unfinished work interrupted and reject cancelled work's late transcripts, text, and audio. Request upstream cancellation where supported, stop pending retries/speech requests, and discard transient audio. Other surfaces' independent turns remain unaffected. The local conversation stays paused until explicit Resume, which does not automatically retry the cancelled question. No text-only completion exception is selected. Cancellation and turn-state ordering require validation.

Step 153 (confirmed): Voice previews use the currently selected interface language only: Thai when the interface is Thai, English when it is English. Do not use a bilingual sample by default or let previewing change the selected language/voice. Exact sample wording, duration, voice IDs, and speaking-speed behavior remain to be defined. Actual TTS support and pronunciation quality for both languages still require route validation.

Step 154 (confirmed): Choose the reply language from the user's typed message, supporting Thai, English, and mixed Thai-English as in voice conversation. Honor explicit requests to reply in a supported language. Do not change the interface or voice-preview language based on chat input. Ordinary typed replies continue to produce text and speech under the existing audio-routing, interruption, memory, access, and usage controls. Actual multilingual route behavior requires validation.

Step 155 (confirmed): Greet in the selected interface language before the first user input in a new conversation. Do not choose greeting language from remembered past conversation language. Once the user speaks or types, adapt under the existing Thai/English, mixed-language, and explicit supported-language request rules. Eligible memory may still personalize greeting content under Step 91, but memory-off greetings must not retrieve prior personal information. Keep greetings brief and play audio only on the originating surface.

Step 156 (confirmed): Newly saved personality presets, traits, and custom instructions apply to the next reply whose generation has not yet begun, without requiring a new conversation. Preserve the personality baseline for a reply already being generated or spoken, including its remaining expressive speech; do not interrupt or regenerate it solely for the edit. Read the latest saved settings for subsequent replies across account surfaces. Access, memory, search, and usage controls retain their existing enforcement timing. Update/generation ordering requires validation; voice/speed changes during speech follow Step 157.

Step 157 (confirmed): Let the current spoken reply finish using its existing voice and speed when new values are saved during speech. Apply the newly saved values to the next reply. Preserve one voice/speed baseline for the whole current reply, including remaining sentences not yet synthesized; do not interrupt, regenerate, or replay it merely for the settings edit. Explicit previews retain their selected pause/cancellation behavior. Provider speed support, baseline capture timing, setting synchronization, and caption alignment require validation.

Step 158 (confirmed): Automatically save changes in Settings > My Companion without a Save button. Cover name, preset, traits, custom instructions, gallery image, selected voice, and speed. Show save status and preserve unsaved drafts for retry on failure while retaining the last saved effective settings. Coalesce rapid edits and validate update ordering/concurrent saves. Previewing a voice does not select/save it. Onboarding retains explicit Continue/Skip and recommendation acceptance. Next-reply application rules apply only to successfully saved values; memory, access, and budget controls retain their existing behavior.

Step 159 (confirmed): Use five discrete labeled levels for playfulness, gentleness, and response length, from Very low to Very high, rather than a 0–100 scale. Localize the labels and make the response-length direction clearly shorter versus more detailed. Proposed storage uses levels 1–5 with no intermediate values. Step 160 subsequently selects initial values; remaining response-length guidance is pending; the confirmed short-answer default, contextual adaptation, custom-instruction precedence, autosave, and preserving saved traits when changing presets still apply.

Step 160 (confirmed): Initialize new accounts with the Warm and gentle preset, Medium playfulness (3/5), High gentleness (4/5), and Short replies (2/5). Short replies retain the approximate one-to-three-sentence style target with context adaptation. Users may change these values later through Settings autosave. Do not reset existing accounts or overwrite saved traits when changing presets.

Step 161 (confirmed): Offer three speaking-speed choices: Slow, Normal, and Fast. Use localized labels and Settings autosave. The current spoken reply retains its existing speed, with the newly saved choice applying to the next reply under Step 157. Step 171 selects Normal as the new-account default. Actual provider values and support for distinct audible speeds require definition and testing against the selected TTS route. Existing voice-preview, caption-alignment, and usage rules still apply.

Step 162 (confirmed): Use the companion's currently saved personality to guide voice-sample delivery, including expressive tone. Apply existing custom-instruction precedence without changing the preview language, voice selection, or saved personality. Do not use failed-save drafts or unaccepted recommendations. No personal-history retrieval or memory learning is required for samples. Preview access/monthly-budget checks, transient audio, and local pause/cancellation behavior remain in effect. Actual expressive quality and settings-to-TTS mapping require validation.

Discovery format update (confirmed): The owner requests ten questions at a time. Steps 163–172 formed the first ten-question batch; the owner has now confirmed the outcomes recorded below. The owner may answer by step number and option number or supply custom choices.

Step 163 (confirmed, option 2): Show History as a list without a user-facing search field.

Step 164 (confirmed, option 1): Order History by latest accepted user conversation activity first. Opening/viewing does not count as conversation activity or reset retention; AI greetings/follow-ups do not move the user-activity timestamp. Use creation time for conversations with no accepted user input and a stable tie-breaker in implementation.

Step 165 (confirmed, option 1): Allow manual renaming of automatically titled conversations. Synchronize the saved title across the account without extending history retention or changing memory. Step 175 preserves a manually saved title through later automatic updates.

Step 166 (confirmed, option 1): Allow selecting multiple History entries and deleting their message histories together, alongside individual deletion. Preserve previously saved personalization memory and summaries under the existing history-deletion policy. Enforce account ownership for every selected entry and prevent stale jobs from reintroducing deleted source content. Step 176 requires confirmation; Step 178 stops a selected active conversation before its history is deleted.

Step 167 (confirmed, option 1): Add a Settings toggle to show/hide AI captions, enabled initially and synchronized across the account. Hiding them does not suppress speech or remove chat text; enabled captions retain the existing alignment and sentence-clearing rules.

Step 168 (confirmed, custom choice): No memory search for users; retain their view/edit/delete and memory-toggle controls. Step 173 limits developer search to the developer account and designated test accounts through scoped local diagnostics. This does not grant the owner access to invitees' private data or authorize AI use of disabled memory.

Step 169 (confirmed, option 1): Use separate Facts/preferences and Conversation summaries tabs within Settings > Memory, preserving existing management actions and the absence of user search.

Step 170 (confirmed, option 1): Add Reset personality: restore Warm and gentle and initial 3/5, 4/5, 2/5 traits, and clear custom instructions. Preserve name, image, voice, speed, history, and memory. This differs from ordinary preset switching, which preserves traits. Save consistently and apply the existing next-reply personality timing; Step 174 requires confirmation before applying the reset.

Step 171 (confirmed, option 1): New accounts start with Normal speaking speed. Preserve existing saved choices; actual provider values and audible speed support require testing.

Step 172 (confirmed, option 1): Limit additional personality instructions to 1,000 characters and show a counter. Preserve unsaved drafts on validation/save failure without silently truncating them. Validate client/server counting, Unicode behavior, and autosave ordering; the character limit is not a token-cost guarantee.

Delegated decisions for Steps 173–182: The owner explicitly asked the assistant to decide this batch using experience and a minimal-budget approach. The selected outcomes below are made under that delegation, not numeric answers supplied by the owner. No paid calls, account creation, purchases, implementation, or deployment were requested by this delegation.

Step 173 (selected under delegation, option 1): Limit developer memory search to the developer's own account and explicitly designated test accounts. Use scoped local development diagnostics rather than adding a user-facing search page or a new admin dashboard. Do not grant access to real invitees' private content through this feature. Enforce the selected account scope and keep privileged credentials out of browser code; exact development tooling requires implementation validation.

Step 174 (selected under delegation, option 1): Confirm Reset personality before applying it. Explain that Warm and gentle and initial traits will be restored and custom personality instructions cleared. Keep name, image, voice, speed, history, and memory. Save the reset consistently and apply the existing next-reply timing.

Step 175 (selected under delegation, option 1): Preserve manually saved conversation titles through later automatic title/summary updates. Recheck the manual-title state before an automatic write so an in-flight title job cannot overwrite a rename. Renaming does not extend retention.

Step 176 (selected under delegation, option 1): Require confirmation before individual or multi-select History deletion. Show the selected title or count and state that saved personalization memory remains. Do not add a delayed-deletion/Undo timer in the initial release. Verify account ownership for all selected entries and apply existing stale-job/source-deletion guards.

Step 177 (selected under delegation, option 1): Require explicit Save when editing an existing memory item or conversation summary; offer Cancel to discard the edit draft. Preserve the draft on save failure and leave the previously saved value effective. Direct Add memory and Enable memory and save this retain their existing explicit-action rules. Companion-settings autosave remains separate. Editing saved records while memory is disabled does not enable memory or authorize AI use of those records.

Step 178 (selected under delegation, option 1): After deletion confirmation, stop all active sessions and unfinished interactive work attached to the selected shared conversation before deleting its message history. Stop capture/playback/captions, close their active-time accounting, release transient audio, and reject late interactive or learning writes derived from the deleted source. Preserve eligible previously saved memory and summaries under the existing policy. Deleting an inactive conversation does not stop unrelated active sessions. Do not automatically create another conversation or restart capture; the user may explicitly start a new conversation or resume another retained thread. Validate stop/deletion ordering and partial failures.

Step 179 (selected under delegation, option 1): Cap a single captured utterance at 120 seconds, accommodating longer companion conversation while bounding transient buffers. At the limit, stop capture and show an explicit Send captured speech or Record again choice rather than silently submitting a clipped statement. Keep audio transient and discard it when abandoned, cancelled, or processing completes. Normal two-second silence detection and hold-release submission still apply before the cap. Validate provider payload/duration limits, device memory, and cap-boundary handling; this desired app limit is not verified STT support.

Step 180 (selected under delegation, option 2): Collect initial private-trial feedback outside the app through the owner's existing manual communication channel. Do not add an in-app report form, feedback database, or delivery integration for this release. This choice does not authorize this assistant to send external messages or collect private conversation content automatically.

Step 181 (selected under delegation, option 1): If the selected TTS route fails actual Thai voice acceptance tests, prepare an OpenRouter alternative with verified capabilities and cost for owner review before adopting it. Preserve the cascaded STT/LLM/TTS architecture. No replacement model has been selected, no test failure is asserted, and this delegation does not authorize paid tests or a silent provider/model change.

Step 182 (selected under delegation, option 1): Allow clearly identified sentence-level captions temporarily in the first prototype if accurate word-to-audio alignment is not ready. Tie the displayed sentence to actual playback and clear it at spoken completion; do not present a guessed typewriter animation as verified word alignment. Preserve progressive word reveal, wrapping, and sentence clearing as the final target. This is a prototype-only exception, not removal of the selected final feature or authorization for extra paid alignment services.

Planning checkpoint - October 6, 2026: Steps 1-172 record owner selections; Steps 173-182 were selected under explicit owner delegation, with initial feedback handled outside the app and temporary sentence-level captions permitted only in the prototype. The planned product remains Laven AI: a voice-first, personalized companion for the owner and allowed invitees, using the selected cascaded OpenRouter pipeline, Next.js/TypeScript, Supabase, and Cloudflare. Proposed implementation defaults are separated from selected requirements in Section 6. Exact model availability, Thai voice quality, speaking-speed support, word-level alignment, end-to-end latency, deployment compatibility, and actual metered costs still need validation. No accounts, purchases, paid tests, app implementation, or deployment have been performed by this blueprint task.
