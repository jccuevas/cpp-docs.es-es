---
title: Uso de parámetros reemplazables (registro ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329230"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Uso de parámetros reemplazables (preprocesador del registrador&#39;s)

Los parámetros reemplazables permiten al cliente de un registrador especificar datos en tiempo de ejecución. Para ello, el registrador mantiene un mapa de reemplazo en el que especifica los valores asociados con los parámetros reemplazables en el script. El registrador realiza estas entradas en tiempo de ejecución.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Uso de %MODULE%

El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) `%MODULE%`genera automáticamente un script que utiliza . ATL utiliza este parámetro reemplazable para la ubicación real del archivo DLL o EXE del servidor.

## <a name="concatenating-run-time-data-with-script-data"></a>Concatenación de datos en tiempo de ejecución con datos de script

Otro uso del preprocesador es concatenar datos en tiempo de ejecución con datos de script. Por ejemplo, supongamos que se necesita una entrada que`, 1`contenga una ruta de acceso completa a un módulo con la cadena " " anexada al final. En primer lugar, defina la siguiente expansión:

```
'MySampleKey' = s '%MODULE%, 1'
```

A continuación, antes de llamar a uno de los métodos de procesamiento de scripts enumerados en [Invocación](../atl/invoking-scripts.md)de scripts , agregue un reemplazo al mapa:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Durante el análisis del script, el `'%MODULE%, 1'` `c:\mycode\mydll.dll, 1`registrador se expande a .

> [!NOTE]
> En un script de registrador, 4K es el tamaño máximo de token. (Un token es cualquier elemento reconocible de la sintaxis.) Esto incluye los tokens creados o expandidos por el preprocesador.

> [!NOTE]
> Para sustituir los valores de reemplazo en tiempo de ejecución, quite la llamada del script a [la](../atl/reference/registry-macros.md#declare_registry_resource) DECLARE_REGISTRY_RESOURCE o [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) macro. En su lugar, `UpdateRegistry` sustitúyalo por su propio método que llame a [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) o [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)y pase la matriz de estructuras _ATL_REGMAP_ENTRY. La matriz de _ATL_REGMAP_ENTRY debe tener al menos una entrada que esté establecida en "NULL,NULL", y esta entrada siempre debe ser la última entrada. De lo contrario, se generará `UpdateRegistryFromResource` un error de infracción de acceso cuando se llame.

> [!NOTE]
> Al compilar un proyecto que genera un ejecutable, ATL agrega automáticamente comillas alrededor del nombre de ruta de acceso creado en tiempo de ejecución con el parámetro de script de registrador **%MODULE%.** Si no desea que el nombre de la ruta de acceso incluya las comillas, utilice el nuevo parámetro **%MODULE_RAW%en** su lugar.
>
> Al compilar un proyecto que genera un archivo DLL, ATL no agregará comillas al nombre de la ruta de acceso si se usa **%MODULE%** o **%MODULE_RAW%.**

## <a name="see-also"></a>Consulte también

[Creación de scripts de registrador](../atl/creating-registrar-scripts.md)
