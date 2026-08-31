# Build 2 Starter Kit — Intelligent Productivity Tool

This kit connects an Apps Script web interface to a temporary pretrained-model server running in Google Colab.

## Files

- `Build_2_Colab_Model_Server.ipynb`: loads Qwen2.5-0.5B-Instruct and creates a verified temporary HTTPS backend.
- `Code.gs`: Apps Script server code. It tests the backend, validates input, calls the model, checks output and fails safely.
- `Index.html`: responsive interface with embedded CSS and JavaScript. It tests the connection before enabling generation and supports editing, approval, rejection and an approved-results list.

## Launch sequence

1. Upload the notebook to Google Colab.
2. Select **Runtime → Restart session**.
3. Run the notebook from top to bottom.
4. Wait for the message **BACKEND READY — ALL AUTOMATIC TESTS PASSED**.
5. Copy the exact base URL and secret printed by that cell.
6. Create a new standalone Apps Script project.
7. Replace the default `Code.gs` with the supplied `Code.gs`.
8. Add an HTML file named `Index` and paste in `Index.html`.
9. Paste the values into `COLAB_API_BASE_URL` and `COLAB_API_SECRET`.
10. Do not add `/health` or `/process` to the base URL.
11. Deploy the Apps Script project as a web app.
12. Open the web app and select **Test connection**.
13. The Generate button becomes available only after Apps Script reaches Colab.
14. Keep Colab connected while testing or demonstrating the app.

## Apps Script deployment

1. Select **Deploy → New deployment**.
2. Select **Web app**.
3. Execute the app as yourself.
4. Select the course-appropriate access setting.
5. Authorize the script when prompted.
6. Open the deployment URL.

After code changes, create a new deployment version or edit the active deployment so the web app receives the changes.

The browser does not need to open the tunnel URL directly. The notebook verifies the public model request first. The web app then performs the connection test through Apps Script.


## Temporary-server limitation

The Colab server and public URL disappear when the runtime disconnects. This is a reproducible prototype rather than permanent hosting. The submission should include a short recording showing the working system and enough instructions to restart it. See Canvas for more instructions on this Build 2 Assignment.

## Privacy

Do not enter confidential, regulated, private or identifying information. The temporary tunnel is public and protected only by a randomly generated shared secret. The secret and temporary URL should not be committed to a public repository.
