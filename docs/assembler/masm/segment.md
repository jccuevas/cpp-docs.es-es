---
title: SEGMENTO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c55416cc5a757128c9cc97b2f342953911ac2946
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32058116"
---
# <a name="segment"></a>SEGMENT
Define un segmento de programa llamado *nombre* con atributos de segmento  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>Parámetros  
 *align*  
 El intervalo de direcciones de memoria desde el que se puede seleccionar una dirección de inicio para el segmento. El tipo de alineación puede ser cualquiera de las siguientes acciones:  
  
|Alinear tipo|Dirección de inicio|  
|----------------|----------------------|  
|**BYTE**|Siguiente dirección de bytes disponibles.|  
|**WORD**|Dirección del próximo word disponible (2 bytes por word).|  
|**DWORD**|Dirección del próximo disponible palabra doble (4 bytes por palabra doble).|  
|**PÁRRAFO**|Siguiente dirección de párrafo disponibles (16 bytes por párrafo).|  
|**PAGE**|Siguiente dirección de página disponible (256 bytes por página).|  
|**ALINEAR**(*n*)|Siguiente disponible *n*direcciones de n bytes. Para obtener más información, vea la sección Comentarios.|  
  
 Si no se especifica este parámetro, **PARA** se utiliza de forma predeterminada.  
  
 *combine*  
 **PÚBLICA**, **pila**, **común**, **memoria**, **en *** dirección*, **privada**  
  
 *Uso*  
 **USE16**, **USE32**, **SIN FORMATO**  
  
 `characteristics`  
 **INFORMACIÓN de**, **leer**, **escribir**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, y **descartar**  
  
 Estos solo se admite para COFF y corresponden a las características de la sección COFF de nombre similar (por ejemplo, **SHARED** corresponde a IMAGE_SCN_MEM_SHARED). LECTURA establece la marca IMAGE_SCN_MEM_READ. La marca de sólo lectura obsoleta provocó la sección Borrar la marca IMG_SCN_MEM_WRITE. Si cualquier `characteristics` están configurados, no se usan las características predeterminadas y solo las marcas especificada por el programador están en vigor.  
  
 `ALIAS(` `string` `)`  
 Esta cadena se utiliza como el nombre de sección en el objeto COFF emitido.  Crea varias secciones con el mismo nombre externo, con distintos nombres de segmento MASM.  
  
 No es compatible con **/omf**.  
  
 `class`  
 Indica cómo segmentos deben combinarse y ordenados en el archivo de ensamblado. Los valores típicos son, `'DATA'`, `'CODE'`, `'CONST'` y `'STACK'`  
  
## <a name="remarks"></a>Comentarios  
 Para `ALIGN(n)`, `n` puede ser cualquier potencia de 2 desde 1 hasta 8192; no se admite con **/omf**.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)