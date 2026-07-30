Note: this information may be outdated. It's based on this challenge:https://github.com/Azr43lKn1ght/DFIR-LABS/tree/main/Covid%20Crime%20Scenario from 2 years ago.
Zoom Data is saved in `C:\Users\username\AppData\Roaming\Zoom\data`.
A folder of the name `smth@smth.zoom.us` or similar with several sqlite databases is useful.
Useful databases and tables (also check other tables, not complete):
- `.zoom.us.db` - in the `zoom_mm_buddy` table, have data about participants
- `.zoom.us.idx.db` - in the `mm_msg_cache_table` table, has sent chat messages
- `.zoom.us.asyn.db` - in the `zoom_mm_file` table has a list of sent files, original path, file name, file size, and the `URL` field which can allow downloading the file.
## Downloading a file
A file is downloaded using the following url:
`https://us02file.zoom.us/zoomfile/download?objkey=URL-FIELD`
In addition, there needs to be a `zmk` header with a private token.
You can get the token by creating a zoom meeting, joining from browser, sending a file (not in browser) and inspecting traffic (Network) in the browser. The `zmk` header can be reused.