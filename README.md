# ikx_backup
## ikx-uploads filename mapping

```bash
├── json
│   ├── ikx.hashbased.json
│   └── ikx.json
└── hash.diff
```

- ikx.json:
  - Original metadata structure.
    - Key: Channel Name
    - Value:
      - hash: hash-coded filename (Current status)
      - ts0: boardcasting start time yyyy-MM-dd
      - ts1: boardcasting start time HH:mm:ss
      - src: source of uploads (e.g. bilibili, youtube, twitcasting...)
      - title: the exact title of the corresponding upload, followed by a boardcasting start time in unix timestamp format  
        **(NOTE: does NOT contain a filename extension)**
        
 - ikx.hashbased.json:
    - Sorted info based on hash code
      - Key: hash code
      - Value:
        - Chn: Channel name (English/Romaji flavor)
        - Src: source of uploads (e.g. bilibili, youtube, twitcasting...)
        - Tit: the exact folder name to remap to, non-ascii chars are unicode formatted.  
          ```
          "\u30102020-09-05\u3011\u301013:01:50\u3011\u3010B\u9650\u3011\u65b0\u7684\u89c6\u89c9\u5c55\u793a\uff01 \u5531\u6b4c\uff01"  
          '【2020-09-05】【13:01:50】【B限】新的视觉展示！ 唱歌！'
          ```
        - Fn: the exact file name to remap to under the 'Tit' Folder, non-ascii chars are unicode formatted.  
          ```
          "\u3010B\u9650\u3011\u65b0\u7684\u89c6\u89c9\u5c55\u793a\uff01 \u5531\u6b4c\uff01_1599310910"  
          '【B限】新的视觉展示！ 唱歌！_1599310910'
          ```
          **(NOTE: does NOT contain a filename extension)**
          
 - hash.diff:
   - Log marking the hash codes which don't match between filename and video_info.json under metadata. Using the previous one (filename) instead.
 
 PS: If a title name is missing in metadata, the default name is "Title_Missing"
 
 
            
