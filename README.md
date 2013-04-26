Freedisk is using `df -h` command. So, it's only available for *nix system like Linux , Unix and Mac OSX ,etc.

#Install

    npm install freedisk

#Example

    var freedisk = require("./freedisk.js");

    freedisk.drivelist(function(error,drives){

        if (error !== null) {
              console.log(error);
        }
        else {

            for (var i = 0; i < drives.length; i++) {

                (function (mydrive) {

                    freedisk.detail(mydrive,function(error,total,used,free){

                        if (error !== null) {
                            console.log(error);
                        }
                        else {
                            //total != used+free because it's using df -h
                            console.log("Drive : " + mydrive);
                            console.log("Total : " + total);
                            console.log("Used : " + used);
                            console.log("Free : " + free);
                        }

                    });//end of detail

                }(drives[i])); // end closure
            }
        }
    });
