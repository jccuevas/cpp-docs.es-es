---
title: Error irrecuperable C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203660"
---
# <a name="fatal-error-c1128"></a>Error irrecuperable C1128

el número de secciones superó el límite de formato de archivo de objeto: compile con /bigobj

Un archivo .obj supera el número de secciones permitidas; ésta es una limitación del formato de archivo objeto COFF.

Llegar a esta sección la limitación puede ser el resultado del uso de [/GY](../../build/reference/gy-enable-function-level-linking.md) y una compilación de depuración; **/GY** hace que las funciones vayan a sus propias secciones COMDAT. En una versión de depuración, hay una sección de información de depuración para cada función COMDAT.

También puede producirse el error C1128 cuando hay demasiadas funciones inline.

Para corregir este error, divida el archivo de origen en varios archivos de código fuente, compile sin **/GY**o compile con [/bigobj (aumente el número de secciones en. Archivo OBJ)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Si no compila con **/GY**, tendrá que especificar las optimizaciones individualmente, ya que **/O2** y **/O1** implican **/GY**.

Si es posible, compile sin información de depuración.

También es posible que necesite disponer de creaciones de instancias de plantillas específicas en archivos de código fuente independientes, en lugar de esperar a que el compilador las emita.

Al migrar código, es probable que C1128 aparezca primero cuando se usa el compilador x64 y, en gran parte, con el compilador de x86. x64 tendrá al menos 4 secciones asociadas a cada función, compilada **/GY** o insertadas a partir de plantillas o clases en línea: código, pdata y información de depuración y, posiblemente, XData.  x86 no tendrá pdata.
