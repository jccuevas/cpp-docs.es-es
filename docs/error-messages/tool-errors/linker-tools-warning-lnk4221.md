---
title: Advertencia de las herramientas del vinculador LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: 299c3ef76006b347d6770d45ca317ff0eb941ffa
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630801"
---
# <a name="linker-tools-warning-lnk4221"></a>Advertencia de las herramientas del vinculador LNK4221

Este archivo objeto no define ningún símbolo público que no se haya definido previamente, por lo que no se usará en ninguna operación de vínculo que consuma esta biblioteca.

Considere los dos fragmentos de código siguientes.

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

Para compilar los archivos y crear dos archivos objeto, ejecute **cl/c a. cpp b. cpp** en un símbolo del sistema. Si vincula los archivos objeto mediante la ejecución de **Link/lib/out: test. lib a. obj b. obj**, recibirá la advertencia LNK4221. Si vincula los objetos ejecutando **Link/lib/out: test. lib b. obj a. obj**, no recibirá ninguna advertencia.

No se emite ninguna advertencia en el segundo escenario porque el enlazador funciona en el último en salir (LIFO). En el primer escenario, b. obj se procesa antes que un. obj y un. obj no tiene símbolos nuevos que agregar. Al indicar al enlazador que procese un. obj en primer lugar, puede evitar la advertencia.

::: moniker range=">=vs-2019"

Una causa común de este error es cuando dos archivos de código fuente especifican la opción [/YC (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) con el mismo nombre de archivo de encabezado especificado en el campo de **encabezado** precompilado. Una causa común de este problema se centra en *PCH. h* , ya que, de forma predeterminada, *PCH. cpp* incluye PCH. *h* y no agrega ningún símbolo nuevo. Si otro archivo de código fuente incluye *PCH. h* con **/YC** y el archivo. obj asociado se procesa antes que PCH. obj, el vinculador producirá LNK4221.

::: moniker-end

::: moniker range="<=vs-2017"

Una causa común de este error es cuando dos archivos de código fuente especifican la opción [/YC (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) con el mismo nombre de archivo de encabezado especificado en el campo de **encabezado** precompilado. Una causa común de este problema trata con *stdafx. h* , ya que, de forma predeterminada, *stdafx. cpp* incluye *stdafx. h* y no agrega ningún símbolo nuevo. Si otro archivo de código fuente incluye *stdafx. h* con **/YC** y el archivo. obj asociado se procesa antes que stdafx. obj, el vinculador producirá LNK4221.

::: moniker-end

Una manera de resolver este problema es asegurarse de que, para cada encabezado precompilado, solo hay un archivo de origen que lo incluye con **/YC**. El resto de los archivos de código fuente deben usar encabezados precompilados. Para obtener más información sobre cómo cambiar esta configuración, vea [/Yu (usar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md).
