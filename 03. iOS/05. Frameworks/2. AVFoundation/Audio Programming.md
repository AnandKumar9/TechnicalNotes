`AVAudioPlayer` can be used for playing audio files.

```
-(void)loadBeepSound{
     NSString *beepFilePath = [[NSBundle mainBundle] pathForResource:@"ding" ofType:@"mp3"];
     NSURL *beepURL = [NSURL URLWithString:beepFilePath];
     NSError *error;
     self.audioPlayer = [[AVAudioPlayer alloc] initWithContentsOfURL:beepURL error:&error];
     self.audioPlayer.delegate = self;
     if (error) {NSLog(@"%@", [error localizedDescription]);}
     else {[self.audioPlayer prepareToPlay];}
}
if (self.audioPlayer) {[self.audioPlayer play];}

There are some optional delegate methods (AVAudioPlayerDelegate) as well.

- (void)audioPlayerDidFinishPlaying:(AVAudioPlayer *)player successfully:(BOOL)flag {
     NSLog(@"Played - %d", flag);
}

- (void)audioPlayerDecodeErrorDidOccur:(AVAudioPlayer *)player error:(NSError *)error {
     NSLog(@"Error - %@", [error localizedDescription]);
}

```
