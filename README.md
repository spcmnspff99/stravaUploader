# stravaUploader

This is an alternative to stravalib if all you want to do is upload files.  It's much smaller and simpler than stravalib. If you pass it a raw tcx or gpx file, it will gunzip the file before uploading.

Requires: requests - pip install requests

Example Usage:

        from stravaUploader import stravaUploader

        su = stravaUploader()

        su.api_key = '<My Strava Access Token>'
        su.format = 'gpx'
        su.filename = 'some_gpx_file.gpx'
        su.private = True
        su.upload()
        if su.duplicate:
            print 'Strava thinks this activity is a duplicate'
        else:   
            #just check the activityid property every second 
            #when it's not None strava is done processing the file
            while True:
                time.sleep(1)
                if su.activityId is not None:
                    break

