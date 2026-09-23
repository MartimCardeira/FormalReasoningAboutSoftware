In case it's needed:

1. Download [this](https://github.com/rocq-prover/platform/releases#release-2025.01.0) version of Coq (latest one which is still called Coq). _change the install directory name to C:\Coq for conveniance_
2. Download the [VsCoq Legacy](https://marketplace.visualstudio.com/items?itemName=coq-community.vscoq1) extension
3. In the extension settings, set the PATH to C:\Coq\bin
4. Download [Unicode Latex](https://marketplace.visualstudio.com/items?itemName=oijaz.unicode-latex) extension
5. Open some .v file, and do Ctrl-shift-p, search `Preferences: Open Workspace Settings (JSON)` and add the following settings:

{

	"coqtop.binPath": "C:\\Coq-Platform~8.17~2023.08\\bin",
	"coq.format.indentAfterBullet": "indent",
	"coq.format.unindentOnCloseProof": true,
	"coq.format.indentAfterOpenProof": true,
	"editor.formatOnType": true,
	"editor.unicodeHighlight.ambiguousCharacters": false,
	"editor.tabSize": 2
}

6. Ctrl-S + Ctr-W to save and close the file
7. Test it out by using alt+down / alt+up to step through the file
