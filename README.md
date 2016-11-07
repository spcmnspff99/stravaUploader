# stravaUploader

This is an alternative to stravalib if all you want to do is upload files.  Its much smaller and simpler than stravalib.

Usage:

        from stravaUploader import stravaUploader

        su = stravaUlploader()

        su.api_key = '<My Strava Access Token>'
        su.format = 'gpx.gz'
        su.filename = 'some_gpx_file.gpx.gz'
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

