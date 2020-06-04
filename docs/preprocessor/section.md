---
title: section (Pragma)
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216601"
---
# <a name="section-pragma"></a>section (Pragma)

Crea una sección en un archivo .obj.

## <a name="syntax"></a>Sintaxis

> **#pragma sección (** "*nombre de sección*" [ **,** *atributos* ] **)**

## <a name="remarks"></a>Comentarios

Los términos *segmento* y *sección* tienen el mismo significado en este artículo.

Cuando se define una sección, sigue siendo válida para el resto de la compilación. Sin embargo, debe utilizar [_ _ declspec (allocate)](../cpp/allocate.md)o no colocar nada en la sección.

*section-Name* es un parámetro necesario que se convierte en el nombre de la sección. El nombre no debe estar en conflicto con ningún nombre de sección estándar. Consulte [/section](../build/reference/section-specify-section-attributes.md) para obtener una lista de los nombres que no se deben usar al crear una sección.

*attributes* es un parámetro opcional que consta de uno o varios atributos separados por comas que se van a asignar a la sección. *Los atributos* posibles son:

|Atributo|DESCRIPCIÓN|
|-|-|
|**read**|Permite operaciones de lectura en los datos.|
|**write**|Permite operaciones de escritura en los datos.|
|**execute**|Permite que el código se ejecute.|
|**shared**|Comparte la sección entre todos los procesos que cargan la imagen.|
|**nopage**|Marca la sección como no paginable. Resulta útil para los controladores de dispositivos Win32.|
|**nocache**|Marca la sección como no almacenable en caché. Resulta útil para los controladores de dispositivos Win32.|
|**discard**|Marca la sección como descartable. Resulta útil para los controladores de dispositivos Win32.|
|**remove**|Marca la sección como no residente en memoria. Solo para los controladores de dispositivos virtuales (V*x*D).|

Si no especifica ningún atributo, la sección tiene atributos de **lectura** y **escritura** .

## <a name="example"></a>Ejemplo

En este ejemplo, la primera sección pragma identifica la sección y sus atributos. El entero `j` no se coloca en `mysec` porque no se declaró con `__declspec(allocate)`. En su lugar `j` , entra en la sección de datos. El entero `i` sí va a `mysec` como resultado de su atributo de clase de almacenamiento `__declspec(allocate)`.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
