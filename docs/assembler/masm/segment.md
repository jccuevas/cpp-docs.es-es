---
title: SEGMENT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 253c3b389bd0411e6b5096e914b6a844c8f40805
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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
|**PARA**|Siguiente dirección de párrafo disponibles (16 bytes por párrafo).|  
|**PAGE**|Siguiente dirección de página disponible (256 bytes por página).|  
|**ALIGN**(*n*)|Siguiente disponible  *n* direcciones de n bytes. Para obtener más información, vea la sección Comentarios.|  
  
 Si no se especifica este parámetro, **PARA** se utiliza de forma predeterminada.  
  
 *combine*  
 **PÚBLICA**, **pila**, **común**, **memoria**, **en *** dirección*, **privada**  
  
 *use*  
 **USE16**, **USE32**, **FLAT**  
  
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