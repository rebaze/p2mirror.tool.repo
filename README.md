# Standalone Eclipse P2 diirector application

## Use with docker
Create a container from the image:
    
    docker create --name p2mirror.tool rebaze/p2mirror.tool bash
    
Then link the volume into your final container: 
Any container with at least Java 7 will do.
e.g. with Jenkins:
    
    docker run  -p 8080:8080 --volumes-from p2mirror.tool jenkins

Now you can use the tool in your Jenkins like so:
    
    /opt/p2mirror/p2.mirror  -nosplash -verbose -application org.eclipse.equinox.p2.artifact.repository.mirrorApplication -source https://bndtools.ci.cloudbees.com/job/bndtools.master/lastSuccessfulBuild/artifact/build/generated/p2 -destination file:$WORKSPACE/mirror
  
## Todo
Currently this repo contains the binary itself, too. Will change once the binary appears in Maven Central.
