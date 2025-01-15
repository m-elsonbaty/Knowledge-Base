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

**Note**: This script uses `2>/dev/null` to suppress permission errors during the search.
