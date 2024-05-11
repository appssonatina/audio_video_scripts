#
# Load echo cancel module
pactl load-module module-echo-cancel aec_method=webrtc source_name=echocancel sink_name=echocancel1

#
# Set module-echo-cancel default source and sink
pacmd set-default-source echocancel
pacmd set-default-sink echocancel1 

