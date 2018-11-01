---
title: component
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: af0e4d7267fab92c867431ab70f4d8a0240a79d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666120"
---
# <a name="component"></a>component
Controla la recopilación de información de examen o información de dependencia en los archivos de código fuente.

## <a name="syntax"></a>Sintaxis

```
#pragma component( browser, { on | off }[, references [, name ]] )
#pragma component( minrebuild, on | off )
#pragma component( mintypeinfo, on | off )
```

## <a name="remarks"></a>Comentarios

### <a name="browser"></a>Explorador

Puede activar o desactivar la recopilación, así como especificar que determinados nombres se omitan al recopilar la información.

El uso de on u off controla la recopilación de información de examen de la pragma hacia delante. Por ejemplo:

```
#pragma component(browser, off)
```

detiene la recopilación de información de examen por parte del compilador.

> [!NOTE]
> Para activar la recopilación de información de examen con esta directiva pragma, [en primer lugar debe habilitarse la información de examen](../build/reference/building-browse-information-files-overview.md).

El `references` opción puede utilizarse con o sin el *nombre* argumento. Uso de `references` sin *nombre* activa o desactiva la recopilación de referencias (sigue siendo recopilados, pero otra información de examen). Por ejemplo:

```
#pragma component(browser, off, references)
```

detiene la recopilación de información de referencia por parte del compilador.

Uso de `references` con *nombre* y `off` evita que las referencias a *nombre* aparezca en la ventana de información de exploración. Utilice esta sintaxis para omitir nombres y tipos en los que no esté interesado y reducir el tamaño de los archivos de información de examen. Por ejemplo:

```
#pragma component(browser, off, references, DWORD)
```

omite las referencias a DWORD desde ese punto en adelante. Puede activar la recopilación de referencias a DWORD activarlo mediante `on`:

```
#pragma component(browser, on, references, DWORD)
```

Esta es la única forma de reanudar la recopilación de referencias a *nombre*; debe activar explícitamente cualquier *nombre* que ha desactivado.

Para evitar que el preprocesador expande *nombre* (por ejemplo, al expandir NULL en 0), inclúyalo entre comillas:

```
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Recompilación mínima

La característica de recompilación mínima de Visual C++ requiere que el compilador cree y almacene la información de dependencia de clase de C++, que ocupa espacio en disco. Para ahorrar espacio en disco, puede usar `#pragma component( minrebuild, off )` cuando no necesite recopilar información de dependencia, por ejemplo, en archivos de encabezado inalterados. Insertar `#pragma component(minrebuild, on)` después de realizar una copia de las clases inalteradas para activar la colección de dependencias en.

### <a name="reduce-type-information"></a>Reducción de la información de tipo

El `mintypeinfo` opción reduce la información de depuración para la región especificada. El volumen de esta información es considerable, afectando a los archivos .pdb y .obj. No puede depurar clases ni estructuras en la región correspondiente a mintypeinfo. El uso de la opción mintypeinfo puede ser útil para evitar la advertencia siguiente:

```
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Para obtener más información, consulte el [habilitar recompilación mínima](../build/reference/gm-enable-minimal-rebuild.md) (/ Gm) opción del compilador.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)