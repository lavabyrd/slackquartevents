# slackquartevents
Events API for Slack based on Quart


## Sample App

```python
from slackquartevents import SlackQuartEventAdapter
from pprint import pprint as print
SLACK_SIGNING_SECRET = ''

slack_events_adapter = SlackQuartEventAdapter(
    SLACK_SIGNING_SECRET, endpoint="/slack/events")

# Create an event listener for "message" events and print the text
@slack_events_adapter.on("message")
async def reaction_added(event_data):

    try:
        text = event_data["event"]['text']
        print(text)
    except KeyError as error:
        print('Invalid key passed to your event payload')
        print(f'Key - {error} is invalid')


# Start the server on port 3000
slack_events_adapter.start(port=3000)

```