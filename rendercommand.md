pandoc -o "Trinidad Aerospace.epub" \
--epub-cover-image=Images/1.png \
--epub-title-page=false \
--css=trinidad.css \
--toc --toc-depth=1 \
"cover.md" \
--toc \
"Trinidad Aerospace - Chapter 1.md" \
"Trinidad Aerospace - Chapter 2.md" \
"Trinidad Aerospace - Chapter 3.md" \
"Trinidad Aerospace - Chapter 4.md" \
"Trinidad Aerospace - Chapter 5.md" \
"Character Reference.md" \
"Set & Setting.md" \
"Chapter Outline.md"
