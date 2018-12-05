### YYPHP Events [GET]
# GET /events
+ Response 200 (application/json)
    + Attributes (array[Event])

# GET /events/{event_id}
+ Parameters
    + event_id: `110977` (string)
+ Response 200 (application/json)
    + Attributes 
        + event: (Event)
        + members: (array)
            + (Member)
                + `user_name`: `スタッフ 名前` (string)
                + `frame_type`: `スタッフ` (string)
            + (Member)
                + `user_name`: `現地参加 名前` (string)
                + `frame_type`: `現地参加` (string)
            + (Member)
                + `user_name`: `リモート参加 名前` (string)
                + `frame_type`: `リモート参加` (string)

## Data Structures

### Event
+ event_id: `110977` (string)
+ event_date: `2018-12-17` (string)
+ title: `#YYPHP #64【PHPの情報交換・ワイワイ話そう・仲間作り・ゆるめ・にぎやかめ】` (string)
+ event_page_url: `https://yyphp.connpass.com/event/110977/` (string)
+ participants: 10 (number)

### Member
+ `icon_url`: `https://connpass-tokyo.s3.amazonaws.com/thumbs/57/4c/574c94930d8e233ca312c0a060114ab6.png` (string)
+ `user_name`: `yamato_ja1461` (string)
+ `frame_type`: `リモート参加` (string)