---
title: Advertencia de las herramientas del vinculador LNK4221
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: b44ba8f0b88beda3e81d9baf59e5348ad4949b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460975"
---
# <a name="linker-tools-warning-lnk4221"></a>Advertencia de las herramientas del vinculador LNK4221

Este archivo de objeto no define los símbolos públicos definidos previamente, por lo que no se utilizará en ninguna vinculación que utilice esta biblioteca

Tenga en cuenta los siguientes fragmentos de código de dos.

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}

```

Para compilar los archivos y crea dos archivos de objeto, ejecute **cl /c a.cpp b.cpp** en un símbolo del sistema. Si vincula los archivos objeto ejecutando **vincular/lib out a.obj b.obj**, recibirá la advertencia LNK4221. Si vincula los objetos mediante la ejecución de **vincular/lib out b.obj a.obj**, no recibirá una advertencia.

Se genera ninguna advertencia en el segundo escenario porque el vinculador funciona de una manera de último en salir (LIFO). En el primer escenario, b.obj se procesa antes que a.obj y a.obj no tiene ningún símbolo nuevo para agregar. Si indica al vinculador que procese a.obj en primer lugar, puede evitar la advertencia.

Una causa común de este error es cuando dos archivos de origen especifican la opción [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) con el mismo nombre de archivo de encabezado especificado en el **encabezado precompilado** campo. Una causa común de este problema se ocupa de stdafx.h ya que, de forma predeterminada, stdafx.cpp incluye stdafx.h y no agrega ningún nuevo símbolo. Si otro archivo de origen incluye stdafx.h con **/Yc** y el archivo .obj asociado se procesa antes que stdafx.obj, el vinculador producirá LNK4221.

Una manera de resolver este problema consiste en asegurarse de que para cada encabezado precompilado, hay solo un archivo de origen que se incluye con **/Yc**. Todos los demás archivos de origen deben utilizar encabezados precompilados. Para obtener más información acerca de cómo cambiar esta configuración, consulte [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md).