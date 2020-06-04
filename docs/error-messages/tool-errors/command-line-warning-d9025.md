---
title: Advertencia de la línea de comandos D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196721"
---
# <a name="command-line-warning-d9025"></a>Advertencia de la línea de comandos D9025

invalidar ' Opción1 ' con ' opción2 '

Se ha especificado la opción *Opción1* pero se ha reemplazado por la *opción2*. Se usó la opción *opción2* .

Si dos opciones especifican directivas contradictorias o incompatibles, se usa la Directiva especificada o implícita en la opción más lejana a la derecha en la línea de comandos.

Si recibe esta advertencia al compilar desde el entorno de desarrollo y no está seguro de dónde proceden las opciones en conflicto, tenga en cuenta lo siguiente:

- Una opción se puede especificar en el código o en la configuración del proyecto del proyecto. Si observa las [páginas de propiedades](../../build/reference/command-line-property-pages.md) de la línea de comandos del compilador y ve las opciones en conflicto en el campo **todas las opciones** , las opciones se establecen en las páginas de propiedades del proyecto, de lo contrario, las opciones se establecen en el código fuente.

   Si las opciones se establecen en las páginas de propiedades del proyecto, mire en la página de propiedades del preprocesador del compilador (con el nodo de proyecto seleccionado en el Explorador de soluciones).  Si no ve la opción establecida allí, Compruebe la configuración de la página de propiedades del preprocesador para cada archivo de código fuente (en Explorador de soluciones) para asegurarse de que no se agrega allí.

   Si las opciones se establecen en el código, se podría establecer en código o en los encabezados de Windows.  Podría intentar crear un archivo preprocesado ([/p](../../build/reference/p-preprocess-to-a-file.md)) y buscar el símbolo.
