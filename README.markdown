This is the master repository for the Sporting Solutions Unified Data API Client for the .Net Framework.

Getting Started
----------------------
	ICredentials credentials = new Credentials { UserName = "jim@bookies", Password = "password" };
	var theSession = SessionFactory.CreateSession(new Uri("http://api.sportingsolutions.com"), credentials);
 
	var theService = theSession.GetService("UnifiedDataAPI");
	var theFeature = theService.GetFeature("Tennis");
	var theResources = theFeature.GetResources();
 
Resources are fixtures/events
 
	var theEvent = theResources.First();
 
	var theSnapshot = theEvent.GetSnapshot();
	System.Console.WriteLine(theSnapshot);
 
	theEvent.StreamConnected += (sender, args) => System.Console.WriteLine("Stream Connected");
	theEvent.StreamEvent += (sender, args) => System.Console.WriteLine(args.Update);
	theEvent.StreamDisconnected += (sender, args) => System.Console.WriteLine("Stream Disconnected");
 
	theEvent.StartStreaming();
 
It really is as easy as that!