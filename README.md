# Final Migrations Project

This project contains migration scripts for transferring data to Wix platform, including blog posts, group posts, events, members and comments.

## Project Structure

```
FinalMigrations/
├── BlogPostsMigration/
├── BlogAndGroupPostsCommentsMigration/ 
├── EventsMigrationFinal/
├── GroupPostsMigrationFinal/
├── MembersMigrationFinal/
└── examples/
```


## Examples
The `examples` directory contains sample files demonstrating the correct data structure for each migration type:

- [`exampleBlogComment.json`](examples/exampleBlogComment.json) - Shows correct blog comment format
- [`exampleBlogPost.json`](examples/exampleBlogPost.json) - Shows correct blog post format
- [`exampleEvent.json`](examples/exampleEvent.json) - Shows correct event format
- [`exampleEventRichContent.json`](examples/exampleEventRichContent.json) - Shows correct event rich content format
- [`exampleGroupComment.json`](examples/exampleGroupComment.json) - Shows correct group comment format
- [`exampleGroupPost.json`](examples/exampleGroupPost.json) - Shows correct group post format

Use these examples to validate your data structure before running migrations.

## Migration Workflows

### 1. Blog Posts Migration
Located in `BlogPostsMigration/`:

1. **Pre-2017 Posts Migration**
   - Main file: [postsMigraionBefore2017.html](BlogPostsMigration/HTML%20FILES/postsMigraionBefore2017.html)
   - Helper files:
     - [extractImages.html](BlogPostsMigration/HTML%20FILES/extractImages.html) - Extracts images from post content
     - [removeFirstDiv.html](BlogPostsMigration/HTML%20FILES/removeFirstDiv.html) - Removes wrapping div from post content

2. **Post-2017 Posts Migration** 
   - Main file: [postMigrationAfter2017.html](BlogPostsMigration/HTML%20FILES/postMigrationAfter2017.html)
   - Helper files:
     - [extractSourceImages.html](BlogPostsMigration/HTML%20FILES/extractSourceImages.html) - Extracts source images

3. **Required Data Files**
   - [wixImages.js](BlogPostsMigration/JS%20FILES/wixImages.js) - Mapped images in Wix media
   - [subjects.js](BlogPostsMigration/JS%20FILES/subjects.js) - Subject mappings
   - [newWritersStudio.js](BlogPostsMigration/JS%20FILES/newWritersStudio.js) - Writer mappings

### 2. Comments Migration
Located in `BlogAndGroupPostsCommentsMigration/`:

1. **Comments Migration Process**
   - Extract images using [extractImages.html](BlogAndGroupPostsCommentsMigration/HTML%20FILES/extractImages.html)
   - Upload images to Wix gallery using the UPLOADIMAGES tool
   - Update [allCommentsImagesUploaded.js](BlogAndGroupPostsCommentsMigration/JS%20FILES/allCommentsImagesUploaded.js)

### 3. Events Migration
Located in `EventsMigrationFinal/`:

1. **Main Migration**
   - [migrate.html](EventsMigrationFinal/HTML%20FILES/migrate.html) - Main migration file
   - Required files:
     - [wixEventsImagesMap.js](EventsMigrationFinal/JS%20FILES/wixEventsImagesMap.js)
     - [right_journey_sections.js](EventsMigrationFinal/JS%20FILES/right_journey_sections.js)
     - [teams.js](EventsMigrationFinal/JS%20FILES/teams.js)

2. **Helper Files**
   - [mapping.html](EventsMigrationFinal/HTML%20FILES/mapping.html) - Helps adapt files to required structure
   - [convertContentToRichContent.html](EventsMigrationFinal/HTML%20FILES/convertContentToRichContent.html)

## Migration Steps

1. **Members Migration**
   - Run members migration first as other migrations depend on user mappings

2. **Blog Posts Migration**
   - Choose appropriate migration file based on post date
   - Extract and upload images before migration
   - Update image mapping files
   - Run migration script

3. **Comments Migration**
   - Extract images from comments
   - Upload images to Wix gallery
   - Update image mappings
   - Run comments migration

4. **Events Migration**
   - Update all required mapping files
   - Run migration script
   - Verify event creation in Wix

## Important Notes

- Always run the migrations in the correct order (Members → Posts → Comments)
- Update mapping files before running migrations
- Verify uploaded images in Wix media library
- Check migrated content in Wix after each migration