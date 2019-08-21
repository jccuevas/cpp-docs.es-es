---
title: Error irrecuperable C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630794"
---
# <a name="fatal-error-c1010"></a>Error irrecuperable C1010

final de archivo inesperado al buscar la directiva de encabezado precompilado. ¿Olvidó agregar ' #include nombre ' al origen?

Un archivo de inclusión especificado con [/Yu](../../build/reference/yu-use-precompiled-header-file.md) no aparece en el archivo de código fuente.  Esta opción está habilitada de forma predeterminada en la C++ mayoría de los tipos de proyecto de Visual Studio y *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores) es el archivo de inclusión predeterminado especificado por esta opción.

En el entorno de Visual Studio, use uno de los métodos siguientes para resolver este error:

- Si no usa encabezados precompilados en el proyecto, establezca la propiedad **crear o usar encabezado** precompilado de archivos de código fuente en **no usar encabezados**precompilados. Para establecer esta opción del compilador, siga estos pasos:

   1. En el panel Explorador de soluciones del proyecto, haga clic con el botón secundario en el nombre del proyecto y, a continuación, haga clic en **propiedades**.

   1. En el panel izquierdo, haga clic en la carpeta **C/C++**  .

   1. Haga clic en el nodo **encabezados** precompilados.

   1. En el panel derecho, haga clic en **crear o usar encabezado**precompilado y, a continuación, haga clic en **no usar encabezados**precompilados.

- Asegúrese de que no ha eliminado accidentalmente, cambiado de nombre o quitado el archivo de encabezado (de forma predeterminada, stdafx. h) del proyecto actual. Este archivo también debe incluirse antes que cualquier otro código de los archivos de código fuente mediante **#include "stdafx. h"** . (Este archivo de encabezado se especifica como **crear/usar PCH a través** de la propiedad de proyecto de archivo)