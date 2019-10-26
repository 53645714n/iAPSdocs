## Branche "développement"

<font color="#FF0000"><strong>Attention:</strong></font>
La branche "développement" est pour les développements ultérieurs d'AndroidAPS seulement. Elle doit être utilisée sur un téléphone séparé pour faire des tests <font color="#FF0000"><strong>mais pas pour la boucle réellement utilisée !</strong></font>

The most stable version of AndroidAPS to use is that in the [Master branch](https://github.com/MilosKozak/AndroidAPS/tree/master). It is advised to stay on the Master branch for actual looping.

The dev version of AndroidAPS is only for developers and testers comfortable dealing with stacktraces, looking through log files and maybe firing up the debugger to produce bug reports that are helpful to the developers (in short: people that know what they are doing without being assisted!). Therefore many unfinished features are disabled. To enable these features enter **Engineering Mode** by creating a file named `engineering_mode` in the same directory where you would find the log files. Enabling the engineering mode might break the loop entirely.

However, the Dev branch is a good place to see what features are being tested and to help iron out the bugs and give feedback on how the new features work in practice. Often people will test the Dev branch on an old phone and pump until they are confident it is stable - any use of it is at your own risk. When testing any new features, remember that you are choosing to test a still-in-development feature. Do so at your own risk & with due diligence to keep yourself safe.

If you find a bug or think something wrong has happened when using the Dev branch, then view the [issues tab](https://github.com/MilosKozak/AndroidAPS/issues) to check whether anyone else has found it, or add it yourself if not. The more information you can share here the better (don't forget you may need to share your [log files](../Usage/Accessing-logfiles.md). The new features can also be discussed in the [gitter room](https://gitter.im/MilosKozak/AndroidAPS).