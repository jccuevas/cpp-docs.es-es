---
title: SEGMENT
ms.date: 12/16/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: 569604bfd6ed11039ce5492223b8d5f986ceea7a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318467"
---
# <a name="segment"></a>SEGMENT

Define un segmento de programa denominado *Name* con atributos de segmento

## <a name="syntax"></a>Sintaxis

> *Name* **Segment** ⟦**ReadOnly**⟧ ⟦*align*⟧ ⟦*combina*⟧ ⟦*use*⟧ ⟦*Characteristics*⟧ **alias (** _String_ **)** ⟦ __'__ *Class* __'__ ⟧ \
> *instrucciones*\
> *nombre* **finaliza**

#### <a name="parameters"></a>Parameters

*alinear*\
El intervalo de direcciones de memoria desde el que se puede seleccionar una dirección inicial para el segmento. El tipo de alineación puede ser cualquiera de los siguientes:

|Alinear tipo|Dirección inicial|
|----------------|----------------------|
|**BYTE**|Siguiente dirección de byte disponible.|
|**WORD**|Siguiente dirección de palabra disponible (2 bytes por palabra).|
|**DWORD**|Siguiente dirección de palabra doble disponible (4 bytes por palabra doble).|
|**PARA**|Siguiente dirección de párrafo disponible (16 bytes por párrafo).|
|**PAGE**|Siguiente dirección de página disponible (256 bytes por página).|
|**Align**(*n*)|Siguiente dirección de *n*bytes disponible. Vea la sección Comentarios para obtener más información.|

Si no se especifica este parámetro, se usa **para** de forma predeterminada.

*combinar* (solo para MASM de 32 bits) \
**Público**, **pila**, **común**, **memoria**, **en**<em>Dirección</em>, **privado**

*use* (solo para MASM de 32 bits) \
**USE16**, **USE32**, **plano**

*características*\
**Info**, **Read**, **Write**, **Execute**, **Shared**, **nopage**, **nocache**y **discard**

Solo se admiten para COFF y se corresponden con las características de la sección COFF de nombre similar (por ejemplo, **Shared** corresponde a IMAGE_SCN_MEM_SHARED). READ establece la marca de IMAGE_SCN_MEM_READ. El marcador de solo lectura obsoleto hizo que la sección borrara la marca IMG_SCN_MEM_WRITE. Si se establece alguna *característica* , no se usan las características predeterminadas y solo se aplican las marcas especificadas por el programador.

_string_\
Esta cadena se usa como nombre de sección en el objeto COFF emitido.  Crea varias secciones con el mismo nombre externo, con distintos nombres de segmento MASM.

No es compatible con **/OMF**.

*class*\
Designa cómo se deben combinar y ordenar los segmentos en el archivo ensamblado. Los valores típicos son, `'DATA'`, `'CODE'`, `'CONST'` y `'STACK'`

## <a name="remarks"></a>Notas

Por `ALIGN(n)`, *n* puede ser cualquier potencia de 2 de 1 a 8192; no es compatible con **/OMF**.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
