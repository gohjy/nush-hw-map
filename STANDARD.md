# Homework Data Standard
```
{
    "class": (string) class name, e.g. "M25102",

    "lastUpdate": (string) last update, e.g. "20250101T12:00:00" - always in SGT,
    
    "url": (string) URL this resource is served from, e.g. "https://yourname.github.io/some-repo-name/path/data.json",

    "homeworkData": [
        {
            "subject": (string) Name of subject as per the timetable, e.g. "EL 1" or "Hum 1",
            
            "courseCode": (string) Course code, e.g. "MA1133" (check github.com/gohjy/nush-pos-data if unsure),
            
            "classId": (string) Class ID, for example for the class "CH1531B" the course code should be "CH1531" and the classID is "B". If the course is taken by mentor class (i.e. the entire cohort is taking it), the classID should be the mentor class e.g. "M25102".,
            
            "items": [
                {
                    "content": (string) Homework content, e.g. "Complete Practice Paper 1 and check answers on Teams: https://v.gd/yourlinksomethingidk" (any link in the format of https://<url>(/path/to/resource)? is acceptable, for example https://example.com or https://example.org/something),

                    "dueDate": (string) due date, e.g. "20251231T12:00:00" - always in SGT (if a homework has several parts with different due dates, put them in different items) (if there is no due time, just a due date, then if applicable put the start of the class timing, if not put 8 a.m.),
                    
                    "optional": (boolean) (optional) true / false. If not given, assumed to be false.

                    If a piece of homework is only applicable to specific people, put such notice in the content field. Do not enter homework data if that piece of homework is only applicable to two-thirds or less of the people taking that course in that class.
                }...

                If there is no homework, the items field should be blank (an empty array).
            ]
        },
        {
            "subject": ditto,
            
            "courseCode": ditto,
            
            "classID": ditto,
            
            "proxy": (boolean) true - always true if present,
            
            "proxyURL": (string) URL to the resource. Useful for things like MTL and elective courses where it's not feasible to have one copy of the data for every mentor class.
        }
        ...
    ]
}
```

For example:
```
{
    "class": "M25102",
    "lastUpdate": "20250101T10:39:00",
    "url": "https://gohjy.github.io/m25102-hw-data/",
    "homeworkData": [
        {
            "subject": "EL 1",
            "courseCode": "EL1131",
            "classID": "M25102",
            "items": [
                {
                    "content": "Read Wonder book - E-copy: v.gd/<this is an example link>",
                    "dueDate": "20250631T00:09:30",
                    "optional": false
                },
                {
                    "content": "Narrative corrections (if undone)",
                    "dueDate": "20250631T00:09:30",
                    "optional": false
                }
            ]
        },
        {
            "subject": "Math 1",
            "courseCode": "MA1133",
            "classID": "M25102"
            "items": []
        },
        {
            "subject": "HCL 1",
            "courseCode": "CH1531",
            "classID": "B",
            "proxy": true,
            "proxyURL": "https://example.com/fictional-json-url/data.json"
        }
    ]
}
```