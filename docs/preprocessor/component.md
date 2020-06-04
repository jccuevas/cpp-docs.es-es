---
title: component (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220469"
---
# <a name="component-pragma"></a>component (Pragma)

Controla la colección de información de exploración o información de dependencias de los archivos de código fuente.

## <a name="syntax"></a>Sintaxis

> **#pragma componente (browser,** { **on** | **OFF** } [ **,** **References** [ **,** *Name* ]] **)**  \
> **componente de #pragma (minrebuild,** { **on** | **OFF** } **)**  \
> **componente de #pragma (mintypeinfo,** { **on** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

### <a name="browser"></a>Browser

Puede activar o desactivar la recopilación, así como especificar que determinados nombres se omitan al recopilar la información.

El uso de on u off controla la recopilación de información de examen de la pragma hacia delante. Por ejemplo:

```cpp
#pragma component(browser, off)
```

detiene la recopilación de información de examen por parte del compilador.

> [!NOTE]
> Para activar la recopilación de información de examen con esta pragma, [primero se debe habilitar la información de examen](../build/reference/building-browse-information-files-overview.md).

La opción References se puede utilizar con o sin el argumento *Name* . El uso de **referencias** sin *nombre* activa o desactiva la recopilación de referencias (sin embargo, se sigue recopilando otra información de exploración). Por ejemplo:

```cpp
#pragma component(browser, off, references)
```

detiene la recopilación de información de referencia por parte del compilador.

El uso de **referencias** con *Name* y **OFF** impide que las referencias a *Name* aparezcan en la ventana de información de examen. Utilice esta sintaxis para omitir nombres y tipos en los que no esté interesado y reducir el tamaño de los archivos de información de examen. Por ejemplo:

```cpp
#pragma component(browser, off, references, DWORD)
```

omite las referencias a DWORD desde ese punto hacia delante. Puede volver a activar la recopilación de referencias a DWORD mediante el uso **de en**:

```cpp
#pragma component(browser, on, references, DWORD)
```

Esta es la única manera de reanudar la recopilación de referencias al *nombre*; debe activar explícitamente cualquier *nombre* que haya desactivado.

Para evitar que el preprocesador expanda el *nombre* (por ejemplo, expandir null hasta 0), coloque comillas alrededor:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Regeneración mínima

La característica [/GM (habilitar recompilación mínima)](../build/reference/gm-enable-minimal-rebuild.md) en desuso requiere que el compilador C++ cree y almacene la información de dependencia de clase, que toma espacio en disco. Para ahorrar espacio en disco, puede usar `#pragma component( minrebuild, off )` siempre que no necesite recopilar información de dependencia, por ejemplo, en archivos de encabezado sin cambiar. Inserte `#pragma component( minrebuild, on )` después de las clases unchanging para volver a activar la colección de dependencias.

### <a name="reduce-type-information"></a>Reducir información de tipos

La `mintypeinfo` opción reduce la información de depuración para la región especificada. El volumen de esta información es considerable, afectando a los archivos .pdb y .obj. No puede depurar clases ni estructuras en la región correspondiente a mintypeinfo. El uso de la opción mintypeinfo puede ser útil para evitar la advertencia siguiente:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Para obtener más información, vea la opción de compilador [/GM (habilitar recompilación mínima)](../build/reference/gm-enable-minimal-rebuild.md) .

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
