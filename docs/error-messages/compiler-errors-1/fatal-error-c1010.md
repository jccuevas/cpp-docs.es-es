---
title: Error irrecuperable C1010
ms.date: 11/04/2016
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 6974f0d82653203973be50b5ea709bd9487a215f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363978"
---
# <a name="fatal-error-c1010"></a>Error irrecuperable C1010

final de archivo inesperado al buscar la directiva de encabezado precompilado. ¿Olvidó agregar ' #include nombre ' para el origen?

Un archivo de inclusión especificado con [/Yu](../../build/reference/yu-use-precompiled-header-file.md) no aparece en el archivo de origen.  Esta opción está habilitada de forma predeterminada en la mayoría de los tipos de proyecto de Visual C++ y "stdafx.h" es el valor predeterminado incluye el archivo especificado por esta opción.

En el entorno de Visual Studio, use uno de los métodos siguientes para resolver este error:

- Si no utiliza encabezados precompilados en su proyecto, establezca el **crear o utilizar encabezado precompilado** propiedad de los archivos de origen **no utilizar encabezados precompilados**. Para establecer esta opción del compilador, siga estos pasos:

   1. En el panel Explorador de soluciones del proyecto, haga clic en el nombre del proyecto y, a continuación, haga clic en **propiedades**.

   1. En el panel izquierdo, haga clic en el **C o C++** carpeta.

   1. Haga clic en el **encabezados precompilados** nodo.

   1. En el panel derecho, haga clic en **crear o utilizar encabezado precompilado**y, a continuación, haga clic en **no utilizar encabezados precompilados**.

- Asegúrese de que accidentalmente no haya eliminado, cambia el nombre o quitar el archivo de encabezado (de forma predeterminada, stdafx.h) del proyecto actual. Este archivo también debe incluirse antes que cualquier otro código en los archivos de origen con **#include "stdafx.h"**. (Este archivo de encabezado se especifica como **crear o utilizar a través de archivo** propiedad de proyecto)