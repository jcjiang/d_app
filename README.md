# d_app

Below and contained within this repo are samples of code I have written in class and at work, mostly the former.

### Potions Work

I worked on a game for a research study regarding rejection bias over the past two terms.  Here are samples of my code for a mechanism that would save certain specific values or location names when the user encounters them within the story.  At the very end, I iterate through the datamap and prints each value to a long URL that allows researchers to see what decisions the players made within the game.

I also wrote JS in Qualtrics to hack the system and implement a reward system that shows certain animations depending on how many previous quizzes were taken, and reward raffle tickets as a bonus to people who complete several quizzes in a roll.

The following is a Twine passage that is displayed/executed when the passage is tagged with a certain keyword, the following inserts the name of the passage into a datamap in order with certain modifications depending on if it was visited in the past.

`<tw-passagedata pid="139" name="putLocation" tags="" position="16,135">{
(set: $oldKey to &quot;a&quot; + (text: $keyL - 1))

(if: (passage:)&#39;s tags contains &quot;recordlocation&quot;)[(set: $valueL to (passage:)&#39;s name)](else: )[]

(if: $values contains $oldKey and $values&#39;s $oldKey contains $valueL)[
    (set: $newVal to $values&#39;s $oldKey +&quot;-r&quot;)
    (set: $values to it + (datamap: $oldKey, $newVal))
](else:)[

(set: $values to it + (datamap: &quot;a&quot; + (text: $keyL), $valueL))

(set: $keyL to it + 1)
(set: $valueL to &quot;&quot;)
]}`

### CS50 Work

At the end of CS50, two other students and I worked on a program that would return and receive commands from a server through threading to solve a maze.  Here are some excerpts of code I wrote for the project.

The following was our left-hand rule method, in which we solved the maze by eventually making every avatar turn left until they found each other.  This contains a possible infinite loop that I fixed in a later commit.

`//check coordinates if they are the same
            if (otherX == myX && otherY == myY) {
              printf("Other Avatar %d is at the same location (%d, %d) as me, Avatar %d!\n", currID, otherX, otherY, avatar->id);
              goalAvatarId = currID;
              noMove = true;

            }
            else {
              printf("Other Avatar %d at (%d, %d) is not at the same location as me, %d (%d, %d)\n", currID, otherX, otherY, avatar->id, myX, myY);
        if (avatarAtGoal(avatar->id, goalAvatarId, response)) {
          avatarMove(avatar, M_NULL_MOVE);
        }
        else if (noMove == true) {
          printf("No move is made because the two avatars are at the same spot\n");
           avatarMove(avatar, M_NULL_MOVE);
        } 
        else {

          // check if the last move from the avatar's last turn worked
          int direction = calculateDirection(avatar->previousMoveDirection, avatar->previousMoveSuccess);
          avatarMove(avatar, direction);
        }`


