# YouTube-Ad-Killer

# YouTube Ad Killer - Browser Bookmarklet Guide

A lightweight, client-side bookmarklet designed to run inside a corporate browser tab to automatically strip out YouTube ad containers, hide display banners, and instantly skip video advertisements without needing extensions or account logins.

---

## Part 1: How to Set Up the Bookmarklet (Do Once)

1. Open your web browser (**Microsoft Edge** or **Google Chrome**).
2. Press `Ctrl + Shift + O` to open your **Bookmarks / Favorites Manager**.
3. Right-click anywhere in your bookmarks list and select **Add page** (or "Add new bookmark").
4. Fill in the following details:
   - **Name:** `YT Ad Killer`
   - **URL / Location:** Paste the exact code block shown below:

```javascript
javascript:((()=>{const s=["ytd-video-masthead-ad-v3-renderer","ytd-engagement-panel-title-header-renderer","ytd-display-ad-renderer","ytd-promoted-sparkles-web-renderer","ytd-compact-promoted-video-renderer","ytd-action-companion-ad-renderer","ytd-banner-promo-renderer",".ad-container",".video-ads"];const t=setInterval(()=>{s.forEach(e=>{document.querySelectorAll(e).forEach(el=>el.remove())});const ad=document.querySelector(".ad-showing"),vid=document.querySelector("video"),skip=document.querySelector(".ytp-ad-skip-button,.ytp-skip-ad-button");if(ad&&vid){vid.currentTime=vid.duration;if(skip)skip.click();}},50);window.yt_killer_interval=t;alert("YouTube Ad Killer active for this tab!");})());

```

5. Click **Save**.
6. Press `Ctrl + Shift + B` to ensure your **Bookmarks Bar** is visible so your new button is easy to click.

---

## Part 2: How to Use It on YouTube

Because corporate browsers restrict background extensions and isolate tab memory, this script runs on a **per-tab basis**. Follow these steps every time you want an ad-free session:

1. Open a new tab and navigate to **YouTube**.
2. Click on the video you want to watch.
3. The moment the page loads, **click your "YT Ad Killer" bookmark** from your bookmarks bar.
4. A quick alert box will pop up saying:
> *"YouTube Ad Killer active!"*
> Click **OK**.


5. **What happens automatically in the background:**
* The script sets up a lightweight loop checking the page every 50 milliseconds.
* Any side banners, promotional blocks, or ad slots are instantly deleted from the DOM.
* If an unskippable video ad triggers (`.ad-showing`), the script immediately fast-forwards the video stream to the very end (`vid.currentTime = vid.duration`) and triggers any available skip buttons instantly.



---

## Troubleshooting & Notes

* **If you change videos or click a link to a new page:** If the page fully reloads or navigates to a brand new URL context, you will need to click the `YT Ad Killer` bookmark button once more on that new tab to re-initialize the loop.
* **Why this works on corporate laptops:** It utilizes native browser JavaScript execution via bookmarks, completely bypassing IT restrictions that block third-party extensions or `.exe` software installations.

```
