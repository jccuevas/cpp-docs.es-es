---
title: Usar parámetros reemplazables (registrador de ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: debbccea5836fa63282b62ff87573160069fb169
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168688"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Usar parámetros reemplazables (el preprocesador del registrador&#39;s)

Los parámetros reemplazables permiten que el cliente de un registrador especifique los datos en tiempo de ejecución. Para ello, el registrador mantiene un mapa de reemplazo en el que especifica los valores asociados a los parámetros reemplazables en el script. El registrador realiza estas entradas en tiempo de ejecución.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Utilizando% MODULE%

El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera automáticamente un script que `%MODULE%`utiliza. ATL usa este parámetro reemplazable para la ubicación real del archivo DLL o EXE del servidor.

## <a name="concatenating-run-time-data-with-script-data"></a>Concatenación de datos en tiempo de ejecución con datos de script

Otro uso del preprocesador es concatenar los datos en tiempo de ejecución con los datos del script. Por ejemplo, supongamos que se necesita una entrada que contiene una ruta de acceso completa a un`, 1`módulo con la cadena "" anexada al final. En primer lugar, defina la siguiente expansión:

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

A continuación, antes de llamar a uno de los métodos de procesamiento de scripts enumerados en [invocación de scripts](../atl/invoking-scripts.md), agregue un reemplazo a la asignación:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Durante el análisis del script, el registrador `'%MODULE%, 1'` se expande a `c:\mycode\mydll.dll, 1`.

> [!NOTE]
> En un script de registrador, 4K es el tamaño máximo del token. (Un token es cualquier elemento reconocible en la sintaxis). Esto incluye los tokens creados o expandidos por el preprocesador.

> [!NOTE]
> Para sustituir los valores de reemplazo en tiempo de ejecución, quite la llamada del script a la macro [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) . En su lugar, reemplácelo por su propio `UpdateRegistry` método que llame a [CAtlModule:: UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)y pase la matriz de estructuras _ATL_REGMAP_ENTRY. La matriz de _ATL_REGMAP_ENTRY debe tener al menos una entrada que esté establecida en {NULL, NULL} y esta entrada siempre debe ser la última entrada. De lo contrario, se generará un error de `UpdateRegistryFromResource` infracción de acceso cuando se llame a.

> [!NOTE]
> Al compilar un proyecto que genera un archivo ejecutable, ATL agrega automáticamente comillas alrededor del nombre de la ruta de acceso creada en tiempo de ejecución con el parámetro de script **% Module%** registrar. Si no desea que el nombre de la ruta de acceso incluya las comillas, use el nuevo parámetro **% MODULE_RAW%** en su lugar.
>
> Al compilar un proyecto que genera un archivo DLL, ATL no agregará comillas al nombre de la ruta de acceso si se usa **% Module%** o **% MODULE_RAW%** .

## <a name="see-also"></a>Consulte también

[Crear scripts de registrador](../atl/creating-registrar-scripts.md)
