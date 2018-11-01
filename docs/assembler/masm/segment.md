---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: f37be47b92a71e20821cd1e40f8cf1350dfedaff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615428"
---
# <a name="segment"></a>SEGMENT

Define un segmento de programa llamado *nombre* tener atributos de segmento

## <a name="syntax"></a>Sintaxis

> *nombre* segmento [[solo lectura]] [[*alinear*]] [[*combinar*]] [[*usar*]] [[*características*]] ALIAS (*cadena*) [['*clase*']]<br/>
> *Instrucciones*<br/>
> *nombre* finaliza

#### <a name="parameters"></a>Parámetros

*align*<br/>
El intervalo de direcciones de memoria desde la que se puede seleccionar una dirección de inicio del segmento. El tipo de alineación puede ser cualquiera de las siguientes acciones:

|Alinear tipo|Dirección inicial|
|----------------|----------------------|
|**BYTE**|Dirección del próximo byte disponible.|
|**WORD**|Siguiente dirección disponible word (2 bytes por word).|
|**DWORD**|Siguiente dirección disponible palabra doble (4 bytes por palabra doble).|
|**PARA**|Dirección del próximo apartado disponibles (16 bytes por párrafo).|
|**PAGE**|Siguiente dirección de página disponible (256 bytes por página).|
|**ALINEAR**(*n*)|Siguiente disponible *n*dirección de bytes th. Para obtener más información, vea la sección Comentarios.|

Si no se especifica este parámetro, **PARA** se usa de forma predeterminada.

*combine*<br/>
**PÚBLICA**, **pila**, **común**, **memoria**, **en**<em>dirección</em>, **Privada**

*Use*<br/>
**USE16**, **USE32**, **SIN FORMATO**

*Características*<br/>
**INFORMACIÓN**, **leer**, **escribir**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, y **descartar**

Estos solo se admiten para COFF y corresponden a las características de la sección COFF de nombre similar (por ejemplo, **SHARED** corresponde a IMAGE_SCN_MEM_SHARED). LECTURA establece la marca IMAGE_SCN_MEM_READ. La marca de solo lectura obsoleta provocó la sección Borrar la marca IMG_SCN_MEM_WRITE. Si cualquier *características* están configurados, no se usan las características de forma predeterminada y solo las marcas especificado por el programador están en vigor.

`ALIAS(` *Cadena* `)`<br/>
Esta cadena se usa como el nombre de sección en el objeto COFF emitido.  Crea varias secciones con el mismo nombre externo, con distintos nombres de segmento MASM.

No es compatible con **/omf**.

*class*<br/>
Designa cómo segmentos deben combinarse y ordenados en el archivo de ensamblado. Los valores típicos son, `'DATA'`, `'CODE'`, `'CONST'` y `'STACK'`

## <a name="remarks"></a>Comentarios

Para `ALIGN(n)`, *n* puede ser cualquier potencia de 2 desde 1 hasta 8192; no se admite con **/omf**.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>