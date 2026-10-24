# VideoDrop privacy

VideoDrop 1.3.2 runs entirely inside Chrome. There is one complete extension, including YouTube and MP3. There is no developer-operated account, analytics, advertising, telemetry, upload endpoint or remote conversion service.

## Browser data and media processing

On HTTP/HTTPS pages, VideoDrop observes media response addresses, content type/size headers, video elements and resource timing entries. It uses the current page title to suggest a filename. Broad website access supports embedded players and video/CDN domains that differ from the page domain. It does not read form fields, passwords, unrelated page text, browser history through the history API, or cookies through the cookies API.

Bounded source addresses/metadata and recent filenames/statuses are held in extension session storage, which clears when the browser session ends. Navigating replaces the tab's source list; closing it removes the list. At most 20 scanned tabs and eight finished records are retained alongside active jobs. Local storage holds two preferences: save-location prompts and support-link visibility. Chrome manages normal download history and saved files independently.

Requested HLS/DASH/file media comes from the source website/CDN using ordinary site cookies where browser policies permit. Temporary rules restore the original page Referer only for the extension's own matching media requests, then are removed after requests/jobs finish. The source receives ordinary network request information. No VideoDrop server receives it.

HLS/DASH tracks are fetched completely and joined by a bundled FFmpeg WebAssembly worker before Chrome saves the file. No remote JavaScript or WebAssembly is loaded. Closing the browser stops preparation and recording.

## Browser-only YouTube support

On a specific YouTube video page, opening VideoDrop requests public session and format metadata from YouTube. Downloading fetches the selected video/audio resources from YouTube's media servers. Their servers receive the requested video identity and ordinary network information, including the connection's IP address.

These requests explicitly omit browser credentials. No account login, browser-cookie import or private-video access is provided. Request-header rules are scoped to the actual installed extension ID and apply only to requests initiated by this extension to YouTube/media hosts. They supply the matching public client headers; ordinary page and other-extension requests are unaffected.

The packaged YouTube.js library parses metadata. Player-script retrieval is disabled: the extension uses complete, directly signed media resources and does not download or execute remote player code. FFmpeg WebAssembly merges video/audio or converts a real MP3 inside Chrome. There is no native helper, executable installer, local network listener or external converter in the 1.3.2 package. Files are saved through Chrome's downloader.

The main extension includes the YouTube module and its extension-scoped header rules.

## Support links and permissions

Patreon and Ko-fi are contacted only when you click their external links. Support is optional; links can be hidden. Those services have their own privacy policies.

- Website access and webRequest discover/request media across HTTP/HTTPS pages, embedded frames and CDN hosts.
- activeTab identifies the current page and suggests its title as a filename.
- downloads saves, tracks, cancels and reveals requested files.
- storage holds bounded session state and local preferences.
- offscreen continues requested media processing while the popup is closed and runs the packaged worker.
- declarativeNetRequestWithHostAccess supplies source-context headers for matching media requests and the extension-scoped YouTube headers described above.

There is no nativeMessaging permission in the current extension package. Removing VideoDrop clears its extension storage. Downloaded files and Chrome's normal download history remain under your control.

Earlier 1.2.0 helper-based archives are historical releases with different behavior documented in their own package. They are not required by or included in 1.3.2.

## Contact

For privacy questions, contact Teirdalin through [Ko-fi](https://ko-fi.com/teirdalin) or [Patreon](https://www.patreon.com/cw/Teirdalin).
