### YYPHP Events [GET]
# GET /api/events
+ Response 200 (application/json)
    + Attributes 
        + events (array)
            + (Event)
                + id: `110977` (string)
                + title: `#YYPHP #64【PHPの情報交換・ワイワイ話そう・仲間作り・ゆるめ・にぎやかめ】` (string)
            + (Event)
                + id: `110978` (string)
                + title: `#YYPHP #65【PHPの情報交換・ワイワイ話そう・仲間作り・ゆるめ・にぎやかめ】` (string)
            + (Event)
                + id: `110979` (string)
                + title: `#YYPHP #66【PHPの情報交換・ワイワイ話そう・仲間作り・ゆるめ・にぎやかめ】` (string)

# GET /api/events/{id}
+ Parameters
    + id: `110977` (string)
+ Response 200 (application/json)
    + Attributes 
        + event: (Event)
            + participants: 6 (number)
        + frames: (array)
            + (Frame)
                + `name`: `スタッフ枠`
                + `members`: (array)
                    + (Member)
                        + `name`: `スタッフ1 名前` (string)
                    + (Member)
                        + `name`: `スタッフ2 名前` (string)
            + (Frame)
                + `name`: `現地参加`
                + `members`: (array)
                    + (Member)
                        + `name`: `現地参加1 名前` (string)
                    + (Member)
                        + `name`: `現地参加2 名前` (string)
                    
            + (Frame)
                + `name`: `リモート参加`
                + `members`: (array)
                    + (Member)
                        + `name`: `リモート参加1 名前` (string)
                    + (Member)
                        + `name`: `リモート参加2 名前` (string)

## Data Structures

### Event
+ id: `110977` (string)
+ event_date: `2018-12-17` (string)
+ title: `#YYPHP #64【PHPの情報交換・ワイワイ話そう・仲間作り・ゆるめ・にぎやかめ】` (string)
+ event_page_url: `https://yyphp.connpass.com/event/110977/` (string)
+ participants: 10 (number)

### Frame
+ `name`: `スタッフ枠`
+ `members`: (array)
    + (Member)

### Member
+ `icon_url`: `https://connpass-tokyo.s3.amazonaws.com/thumbs/57/4c/574c94930d8e233ca312c0a060114ab6.png` (string)
+ `name`: `yamato_ja1461` (string)

