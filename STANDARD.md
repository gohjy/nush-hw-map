# Homework Data Standard
```
{
    "class": (string) class name, e.g. "M25102",

    "lastUpdate": (string) last update, e.g. "2025-01-01T12:00:00" - always in SGT (implied +08:00 to the end),
    
    "url": (string) URL this resource is served from, e.g. "https://yourname.github.io/some-repo-name/path/data.json",

    "homeworkData": [
        {
            "subject": (string) Name of subject as per the timetable, e.g. "EL 1" or "Hum 1",
            
            "courseCode": (string) Course code, e.g. "MA1133" (check github.com/gohjy/nush-pos-data if unsure),
            
            "classId": (string) Class ID, for example for the class "CH1531B" the course code should be "CH1531" and the classID is "B". If the course is taken by mentor class (i.e. the entire cohort is taking it), the classID should be the mentor class e.g. "M25102".,
            
            "items": [
                {
                    "type": (string) "homework",


                    "content": (string) Homework content, e.g. "Complete Practice Paper 1 and check answers on Teams: https://v.gd/yourlinksomethingidk" (any link in the format of https://<url>(/path/to/resource)? is acceptable, for example https://example.com or https://example.org/something),

                    "dueDate": (string) due date, e.g. "20251231T12:00:00" - always in SGT (if a homework has several parts with different due dates, put them in different items) (if there is no due time, just a due date, then if applicable put the start of the class timing, if not put 8 a.m.),
                    
                    "optional": (boolean) (optional) true / false. If not given, assumed to be false.

                    If a piece of homework is only applicable to specific people, put such notice in the content field. Do not enter homework data if that piece of homework is only applicable to two-thirds or less of the people taking that course in that class.
                },
                {
                    "type": (string) "info",

                    "content": (string) info content

                    Use this for providing general info relating to that subject, e.g. linking to an admin post on Teams. Note that admin announcements (not related to a specific subject) like SMO signups, class rules, relief teacher updates etc should NOT go in the homework file.
                }

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

When there is a need to put a link inside the data, do shorten any long links (longer than 20 characters). You are recommended to use [v.gd](https://v.gd) to shorten links, and those who implement software to read the data are recommended to convert all v.gd links into clickable links. *(You can add - to the end of a v.gd link to display a preview, for example [https://v.gd/meanie-](https://v.gd/meanie-).)*

Do note that adding any inappropriate content to the repo (e.g. sexually explicit content or content encouraging terrorism) can and will cause your repo to be removed from the nush-hw-map, as well as potentially reported to GitHub and/or the relevant authorities.

---

Example of implementation of standard:
```
{
    "class": "M25102",
    "lastUpdate": "2025-01-01T10:39:00",
    "url": "https://gohjy.github.io/m25102-hw-data/",
    "homeworkData": [
        {
            "subject": "EL 1",
            "courseCode": "EL1131",
            "classID": "M25102",
            "items": [
                {
                    "type": "homework",
                    "content": "Read Wonder book - E-copy: v.gd/<this is an example link>",
                    "dueDate": "20250631T00:09:30",
                    "optional": false
                },
                {
                    "type": "homework",
                    "content": "Narrative corrections (if undone)",
                    "dueDate": "20250631T00:09:30",
                    "optional": false
                },
                {
                    "type": "info",
                    "content": "For more information, please see Teams post: v.gd/INSERT_LINK_HERE"
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
