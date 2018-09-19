---
title: Error del compilador de recursos RC2104 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2104
dev_langs:
- C++
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd602dcde34aa7cc08486188ab5fb5925eca0eb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081096"
---
# <a name="resource-compiler-error-rc2104"></a>Error del compilador de recursos RC2104

palabra clave o nombre de clave sin definir: clave

La palabra clave o el nombre de clave especificados no se ha definido.

A menudo, este error se debe a un error de escritura en la definición del recurso o en el archivo de encabezado incluido. También puede deberse a que falta un archivo de encabezado.

Para corregir el problema, busque el archivo de encabezado que debe contener la palabra clave o el nombre de clave definidos y compruebe que se han incluido en el archivo de recursos, y que la palabra clave o el nombre de clave están escritos correctamente. Si el proyecto se creó con un encabezado precompilado y posteriormente lo eliminó, asegúrese de que el archivo de recursos sigue incluyendo los encabezados necesarios.

Para comprobar las palabras clave definidas y nombres de clave en el archivo de recursos, en Visual Studio, abra el **vista de recursos** ventana, en la barra de menús, elija **vista**, **vista de recursos**: y a continuación, abra el menú contextual para el archivo .rc y elija **símbolos de recursos** para ver la lista de símbolos definidos. Para modificar los encabezados incluidos, abra el menú contextual para el archivo .rc y elija **incluye recursos**.

Si aparece este mensaje:

```
undefined keyword or key name: MFT_STRING
```

abra \MCL\MFC\Include\AfxRes.h y agregue esta directiva Include:

```
#include <winresrc.h>
```