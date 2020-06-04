---
title: Error del compilador de recursos RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: d4a06f88e4a73da6b711d108a1f79c14fae0907c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191644"
---
# <a name="resource-compiler-error-rc2104"></a>Error del compilador de recursos RC2104

palabra clave o nombre de clave sin definir: clave

La palabra clave o el nombre de clave especificados no se ha definido.

A menudo, este error se debe a un error de escritura en la definición del recurso o en el archivo de encabezado incluido. También puede deberse a que falta un archivo de encabezado.

Para corregir el problema, busque el archivo de encabezado que debe contener la palabra clave o el nombre de clave definidos y compruebe que se han incluido en el archivo de recursos, y que la palabra clave o el nombre de clave están escritos correctamente. Si el proyecto se creó con un encabezado precompilado y posteriormente lo eliminó, asegúrese de que el archivo de recursos sigue incluyendo los encabezados necesarios.

Para comprobar las palabras clave y los nombres de clave definidos en el archivo de recursos, en Visual Studio, abra la ventana de **vista de recursos** (en la barra de menús, elija **Ver**, **vista de recursos**) y, a continuación, abra el menú contextual del archivo. RC y elija **símbolos de recursos** para ver la lista de símbolos definidos. Para modificar los encabezados incluidos, abra el menú contextual del archivo. RC y elija archivos de **inclusión de recursos**.

Si aparece este mensaje:

```
undefined keyword or key name: MFT_STRING
```

abra \MCL\MFC\Include\AfxRes.h y agregue esta directiva Include:

```
#include <winresrc.h>
```
