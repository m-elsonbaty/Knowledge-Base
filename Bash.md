## Automating File Search and Cleanup

### Bash Script for File Search and Cleanup

The following Bash script automates file search and cleanup:

```bash
#!/bin/bash

# Search for files with "test" in the name
file_count=$(find / -type f -name "*test*" 2>/dev/null | wc -l)
echo "Files with word 'test' in name found: $file_count"

# Search for files containing "test" in their content
content_count=$(grep -rl "test" / 2>/dev/null | wc -l)
echo "Files with word 'test' in content found: $content_count"

# Delete files with "test" in the name, older than 2 weeks
find / -type f -name "*test*" -mtime +14 -exec rm -f {} \; 2>/dev/null
echo "Files with 'test' in name, older than 2 weeks, have been deleted."
```

### Script Explanation:
1. **Search for files with "test" in the name**:
   - The `find` command locates files matching the pattern `*test*`.
   - `wc -l` counts the total number of matching files.

2. **Search for files containing "test" in content**:
   - The `grep` command recursively searches for the word "test" in file content.

3. **Delete files older than 2 weeks**:
   - The `find` command filters files by name and age (`-mtime +14`) and removes them with `-exec rm -f`.

**Note**: This script uses `2>/dev/null` to suppress permission errors during the search.
