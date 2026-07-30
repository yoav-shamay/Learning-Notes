- https://fastdl.app/en2 can help with downloading profile picture (put user url)
## Google Search
https://www.aware-online.com/en/osint-tutorials/view-private-instagram-accounts/
search in google `"instagram.com/p" "profile_name"`
results can show part of posts.
Alternative: `site:instagram.com profile_name`.
Changing the search query and adding some words might allow seeing data related to those words in the preview.

A trick that worked for me was copying the preview lines, adding just `instagram profile_name`, and it allowed to see a bit more. repeating it with only the end of the added part allowed extracting a bit of the data of the post. usually stops in `...more` or smth.
Alternatively do the same but with the post ID instead of `instagram profile_name`.
Might require a full sentence to actually work, experiment a bit.

Some other stuff to try:
- `"instagram" "user_name"`
- `instagram user_name`
- `"instagram" "user_name" username's profile picture` - to see some metadata afterwards.

## Wayback machine
- You can try putting posts / profiles in wayback machine if it was public at some point.