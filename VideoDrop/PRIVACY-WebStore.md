# VideoDrop privacy — Chrome Web Store edition

Updated October 27, 2026. This policy applies to VideoDrop 1.3.3 Web Store and later store releases with the same behavior.

VideoDrop runs entirely inside Chrome. It has no developer-operated account, analytics, advertising, telemetry, upload endpoint or remote conversion service. YouTube downloading is not supported. Its provider and library are not included, and extension requests to YouTube and its media hosts are blocked.

## Browser data and media processing

On supported HTTP/HTTPS pages, VideoDrop observes media response addresses, content type/size headers, video elements and resource timing entries. The current page title suggests a filename. Website access supports embedded players and CDN hosts separate from the page. It does not read passwords, form fields, unrelated page text, browser history through the history API, or cookies through the cookies API.

Bounded source metadata, filenames and recent statuses stay in extension session storage, cleared when the browser session ends. Navigation replaces the source list; closing a tab removes it. At most 20 scanned tabs and eight finished records are retained alongside active jobs. Local storage holds save-location and support-link preferences. Chrome manages normal download history and files independently.

User-requested file/HLS/DASH media comes from its source website/CDN, using ordinary site cookies where browser policies permit. Temporary rules restore the source-page Referer for this extension’s matching requests and are removed after requests/jobs finish. Source servers receive ordinary network information, including the connection’s IP address. No VideoDrop server receives it.

The bundled FFmpeg WebAssembly worker joins media tracks locally. No remote code is loaded. Closing Chrome stops preparation and live capture. Prepared media has a combined 512 MB input limit.

## Permissions and optional support

- Website access and webRequest discover/fetch supported media across pages, frames and CDN hosts.
- activeTab identifies the page used for the download and suggested filename.
- downloads saves, tracks, cancels and reveals requested files.
- storage holds bounded session state and local preferences.
- offscreen continues requested processing after the popup closes.
- declarativeNetRequestWithHostAccess provides temporary source-referrer rules and blocks extension-initiated requests to excluded YouTube hosts. Earlier YouTube-specific header rules are removed on update.

Patreon and Ko-fi open only when clicked; support is optional and links can be hidden. These services apply their own privacy policies. Contact Teirdalin through [Ko-fi](https://ko-fi.com/teirdalin) or [Patreon](https://www.patreon.com/cw/Teirdalin).

Uninstalling clears extension storage. Downloaded files and Chrome’s normal download history remain under your control.