---
title: Usar parámetros reemplazables (registrador de ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 1c772c0493b351d8452400a4fb1e3949ab6f28f2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814038"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Usar parámetros reemplazables (el registrador&#39;s preprocesador)

Parámetros reemplazables permiten que un cliente del registrador especificar los datos de tiempo de ejecución. Para ello, el registrador mantiene un mapa de reemplazo en el que escribe los valores asociados con los parámetros reemplazables en el script. El registrador realiza estas entradas en tiempo de ejecución.

##  <a name="_atl_using_.25.module.25"></a> Usar el módulo %

El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera automáticamente un script que usa `%MODULE%`. ATL utiliza este parámetro reemplazable para la ubicación real del archivo DLL o EXE de su servidor.

## <a name="concatenating-run-time-data-with-script-data"></a>Concatenar datos en tiempo de ejecución con datos de secuencia de comandos

Otro uso del preprocesador es concatenar datos de tiempo de ejecución con datos de secuencia de comandos. Por ejemplo, supongamos que se necesita una entrada que contiene una ruta de acceso completa a un módulo con la cadena "`, 1`" anexado al final. En primer lugar, defina la expansión de la siguiente:

```
'MySampleKey' = s '%MODULE%, 1'
```

A continuación, antes de llamar a uno de los métodos enumerados en el procesamiento de scripts [invocar Scripts](../atl/invoking-scripts.md), agregue un reemplazo al mapa:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Durante el análisis de la secuencia de comandos, se expande el registrador `'%MODULE%, 1'` a `c:\mycode\mydll.dll, 1`.

> [!NOTE]
>  En un script de registrador, 4K es el tamaño máximo del token. (Un token es cualquier elemento reconocible en la sintaxis). Esto incluye los tokens que se crearon o el preprocesador expande.

> [!NOTE]
>  Para sustituir los valores de reemplazo en tiempo de ejecución, quite la llamada en el script para la [macros DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) o [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) macro. En su lugar, reemplácelo por los suyos propios `UpdateRegistry` método que llama a [CAtlModule:: UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)y pase la matriz de _ATL_REGMAP_ Estructuras de entrada. La matriz de _ATL_REGMAP_ENTRY debe tener al menos una entrada que se establece en {NULL, NULL}, y esta entrada debe ser siempre la última entrada. En caso contrario, será un error de infracción de acceso generadas cuando `UpdateRegistryFromResource` se llama.

> [!NOTE]
>  Al compilar un proyecto que genera un archivo ejecutable, ATL agrega automáticamente las comillas alrededor del nombre de ruta de acceso creado en tiempo de ejecución con el **% MODULE %** parámetro de secuencia de comandos del registrador. Si no desea que el nombre de ruta de acceso para incluir las comillas, use la nueva **% MODULE_RAW %** parámetro en su lugar.
>
>  Al compilar un proyecto que genera un archivo DLL, ATL no agregará las comillas en el nombre de ruta de acceso si **% MODULE %** o **% MODULE_RAW %** se utiliza.

## <a name="see-also"></a>Vea también

[Crear scripts del registrador](../atl/creating-registrar-scripts.md)
