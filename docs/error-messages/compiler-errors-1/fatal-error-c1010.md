---
title: Error irrecuperable C1010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae762c15c96ed7c12a20d2070d22cdc556667ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064092"
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