# Installations Guide Pytorch + Cuda für Nvidia RTX2070

- für die RTX2070 wird Cuda 10.2 verwendet (höhere Versionen nicht unterstützt!?)
- für Cuda 10.2 die torch version 1.10.1 verwendet
- torch version 1.10.1 läuft nur bis python 3.9 (3.10 nicht möglich)

## pipenv
Die direkte Installation aus dem Pipfile führt zu einer Fehlermeldung. Ein paar Foren melden Fehler von Pipenv, der Workaround war 
die pipenv ohne pytorch zu installieren und torch+cuda separate zu installieren:
- entferne pytorch aus dem Pipfile 
- installiere pipenv `pipenv install`
- aktiviere pipenv `pipenv shell`, verlasse die shell `exit`
- installiere torch+cuda `pipenv install --extra-index-url https://download.pytorch.org/whl/ "torch==1.10.1+cu102"` [forum](https://github.com/pypa/pipenv/issues/4961)

Die Fehlermeldung / Warnung erscheint zwar immer noch, aber die Installation ist durch und das `pytorch_gpu_tests` file zeigt dass 
die GPU gefunden wird mit Cuda==TRUE.

**Fehlermeldung / Warnung**  
[pipenv.exceptions.ResolutionFailure]: Warning: Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.
You can use $ pipenv install --skip-lock to bypass this mechanism, then run $ pipenv graph to inspect the situation.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: No matching distribution found for torch==1.10.1+cu102



