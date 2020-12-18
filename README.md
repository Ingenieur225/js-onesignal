<script src="https://cdn.onesignal.com/sdks/OneSignalSDK.js" async=""></script>
        <script>
            // INITIALISATION DE LA NOTIFICATION
            window.OneSignal = window.OneSignal || [];
            OneSignal.push(function() {
                OneSignal.init({
                    appId: "f0fcb86c-5c1a-4fb1-9358-3e28cadee5bb"
                });
            });

            // VERIFIER SI LE NAVIGATEUR EST SUPPORTER
            OneSignal.push(function() {
                /* These examples are all valid */
                var isPushSupported = OneSignal.isPushNotificationsSupported();
                if (isPushSupported) {
                    // Push notifications are supported
                    console.log('Le navigateur est supporté');

                    OneSignal.isPushNotificationsEnabled(function(isEnabled) {
                        if (isEnabled) {
                            console.log("Push notifications are enabled!");
                            
                            // OBTENIR L'ID DE L'UTILISATEUR
                            OneSignal.getUserId(function(userId) {
                                console.log("OneSignal User ID:", userId);

                                // ON ASSIGNE LE USER ID AU CLIENT CONNECTE AFIN DE L'ENVOYER UNE NOTIFICATION
                                document.getElementById('user_id').value = userId;
                            });




                            // FUNCTION RANDOM
                            // var dt = new Date().getTime();
                            // var uuid = 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'.replace(/[x]/g, function(c) {
                            //     var r = (dt + Math.random()*16)%16 | 0;
                            //     dt = Math.floor(dt/16);
                            //     return (c=='x' ? r :(r&0x3|0x8)).toString(16);
                            // });
                            
                            // // GENERER UN UNIQUE PLAYER ID 
                            // $value_ = OneSignal.setExternalUserId(uuid);
                            // console.log("OneSignal User ID:", value_);
                            // document.getElementById('user_id').value = value_;
                        }
                        else {
                            console.log("Push notifications are not enabled yet.");

                            // AFFICHAGE DE L'ALERTE
                            OneSignal.push(function() {
                                OneSignal.showHttpPrompt();
                            });

                        }    
                    });
                } else {
                    // Push notifications are not supported
                    console.log('Le navigateur n\'est pas supporté');
                }
            });

        </script>
