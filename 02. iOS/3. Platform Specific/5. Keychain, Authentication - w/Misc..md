Code snippet for touch ID -

```
NSError *error = nil;
LAContext *context = [LAContext new];

if ([context canEvaluatePolicy:LAPolicyDeviceOwnerAuthenticationWithBiometrics error:&error]) {

    [context evaluatePolicy:LAPolicyDeviceOwnerAuthenticationWithBiometrics
            localizedReason:@"Are you the device owner?"
                      reply:^(BOOL success, NSError *error) {
                          if (success) {
                              dispatch_async(dispatch_get_main_queue(), ^{
                                  UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:@"Success"
                                                                                      message:@"User should be logged in after this"
                                                                                     delegate:self
                                                                            cancelButtonTitle:@"OK"
                                                                            otherButtonTitles:nil, nil];
                                  [alertView show];

                              });
                          }
                          else {
                              dispatch_async(dispatch_get_main_queue(), ^{
                                  NSLog(@"Fails with error code %ld", error.code);
                                  if (error.code != LAErrorAuthenticationFailed && error.code != LAErrorUserCancel) {
                                   // Do what you want
                                  }
                              });
                          }
                      }];
}
else {
    NSLog(@"Cannot evaluate");
}

```
