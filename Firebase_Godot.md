# Firebase Analytics for Godot — Guide & Stubs

This document explains how to add Firebase analytics to the Godot prototype and includes a simple `firebase_stub.gd` for event logging.

Why use analytics
- Track retention (D1/D7), session length, rewarded ad engagement, purchase funnels, and event conversions.

Options for Godot
- Use community plugins that wrap Firebase SDKs for Android/iOS (search for `godot-firebase` compatible with Godot 4.x).  
- Alternatively, send events to a small server endpoint that forwards events to Firebase via the Admin SDK (safer for some server-side validations).

Sample events to log (from GDD)
- `session_start`
- `coins_collected`
- `building_built`
- `building_upgraded`
- `ad_watched`
- `purchase_made`
- `subscription_started`
- `grid_unlocked`
- `event_participated`

Sample GDScript stub (`firebase_stub.gd`)
```gdscript
extends Node

func log_event(event_name: String, params: Dictionary = {}):
    # Replace with plugin code to send to Firebase
    print("[Analytics] log_event: %s %s" % [event_name, str(params)])

func set_user_property(name: String, value: String):
    print("[Analytics] set_user_property: %s = %s" % [name, value])

func initialize():
    print("[Analytics] firebase_stub initialized")
```

Integration tips
- Keep analytics calls small and non-blocking.  
- Use event batching if sending to a server to reduce network overhead.  
- Don't log PII (personally identifiable information) without proper consent.

Testing
- Verify events in Firebase DebugView and Analytics console.  
- Use staged releases/TestFlight to test event flows before global launch.

Further reading
- Firebase Analytics docs: https://firebase.google.com/docs/analytics
