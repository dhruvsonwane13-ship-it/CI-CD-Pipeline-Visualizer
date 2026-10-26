# CI/CD Pipeline Visualizer

A beginner-friendly, interactive visual guide to the journey from a developer's code change to a monitored production release. The project uses a red-and-black theme and credits **Dhruv Sonawane**.

## What it shows

- Eight clickable pipeline stages with plain-language explanations.
- An animated SVG diagram, step navigation, auto-play (5 seconds per stage), and reset.
- A red/black visual theme, page light-mode toggle, responsive layout, and reduced-motion support.
- No build step, package manager, or JavaScript dependencies.

## Moving objects

| Object | Meaning |
| --- | --- |
| Code change | A developer's source-code update |
| Build artifact | The packaged output created by the build job |
| Test report | Automated test results used to decide whether to continue |
| Deployment package | A verified application release moving toward an environment |
| Failure / rollback | A problem detected after release and the path back to a stable version |

## The 8 steps

1. **Plan and code** — a developer changes the application and saves the work.
2. **Continuous Integration** — a push or pull request starts an automated pipeline.
3. **Build** — source code is turned into a reusable artifact.
4. **Automated tests** — checks find issues before release; failed checks should stop the pipeline.
5. **Container image** — the application and its dependencies are packed into a Docker image and stored in a registry.
6. **Deploy to staging** — the candidate release is tested in a safe environment.
7. **Deploy to production** — the approved version is released to users.
8. **Monitor and rollback** — logs, metrics, and alerts help the team detect issues and return to a stable version if needed.

## Run locally

From inside the `cicd-pipeline` folder, run:

```bash
python3 -m http.server 8000
```

Open <http://localhost:8000> in your browser. (On Windows, `py -m http.server 8000` may also work.)

## Host on GitHub Pages

1. Create a GitHub repository named `cicd-pipeline`.
2. Upload the **contents** of this folder to the repository's `main` branch, with `index.html` at the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch **main** and folder **/ (root)**, then click **Save**.
6. Wait for deployment and open `https://YOUR-USERNAME.github.io/cicd-pipeline/` (replace `YOUR-USERNAME` with your GitHub username).

## Project structure

```text
cicd-pipeline/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── app.js
├── .nojekyll
├── LICENSE
└── README.md
```

## Customise text and colours

- **Step text:** edit the `steps` array in `js/app.js`.
- **Diagram layout:** update the `nodes` array and SVG drawing helpers in `js/app.js`.
- **Theme colours:** change CSS variables at the top of `css/style.css`. The main red accent is `--red`; page and panel backgrounds use `--page`, `--panel`, and `--panel2`.
- **Creator name:** search for `Dhruv Sonawane` in `index.html` and `README.md`.
- **Motion:** SVG packet motion is in `js/app.js`; reduced-motion preferences are respected.

## Note

This is an educational visualizer, not a working CI/CD service. Real pipelines need configured source-control triggers, build runners, test commands, registries, deployment credentials, monitoring, and rollback automation.
