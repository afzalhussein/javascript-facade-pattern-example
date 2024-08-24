# javascript-facade-pattern-example
The Facade Pattern is a structural design pattern that provides a simplified interface to a complex system, making it easier to interact with. It hides the complexities of the underlying system by providing a unified interface that clients can use. In JavaScript, it's commonly used to simplify interaction with multiple subsystems or to provide a more straightforward API for a complex system.

Here's a JavaScript example illustrating the Facade Pattern:

Suppose you have a complex subsystem involving multiple classes/functions that you want to simplify using a Facade. Let's consider a multimedia system involving various components like an audio player, a video player, and a display manager.

```javascript
// Subsystem - AudioPlayer
class AudioPlayer {
  play() {
    console.log('Audio playing');
  }

  stop() {
    console.log('Audio stopped');
  }
}

// Subsystem - VideoPlayer
class VideoPlayer {
  play() {
    console.log('Video playing');
  }

  stop() {
    console.log('Video stopped');
  }
}

// Subsystem - DisplayManager
class DisplayManager {
  open() {
    console.log('Display opened');
  }

  close() {
    console.log('Display closed');
  }
}

// Facade - MultimediaFacade
class MultimediaFacade {
  constructor() {
    this.audioPlayer = new AudioPlayer();
    this.videoPlayer = new VideoPlayer();
    this.displayManager = new DisplayManager();
  }

  playAudio() {
    this.audioPlayer.play();
    this.displayManager.open();
  }

  stopAudio() {
    this.audioPlayer.stop();
    this.displayManager.close();
  }

  playVideo() {
    this.videoPlayer.play();
    this.displayManager.open();
  }

  stopVideo() {
    this.videoPlayer.stop();
    this.displayManager.close();
  }
}

// Client code
const multimediaFacade = new MultimediaFacade();

// Using the facade to play audio and video
multimediaFacade.playAudio(); // This will play audio and open the display
multimediaFacade.stopAudio(); // This will stop audio and close the display
multimediaFacade.playVideo(); // This will play video and open the display
multimediaFacade.stopVideo(); // This will stop video and close the display
```

In this example:

- `AudioPlayer`, `VideoPlayer`, and `DisplayManager` are subsystems representing different components of a multimedia system.
- `MultimediaFacade` provides a simple interface for interacting with these subsystems. It encapsulates the complex operations involving multiple subsystems and provides easy-to-use methods for clients.
- Clients interact with the `MultimediaFacade` instead of directly dealing with the complexities of the subsystems.

The Facade Pattern allows clients to use a simplified interface provided by the facade class (`MultimediaFacade` in this case), abstracting away the complexities of the underlying subsystems. It promotes loose coupling between the client and the subsystems, making the code more maintainable and easier to understand.
