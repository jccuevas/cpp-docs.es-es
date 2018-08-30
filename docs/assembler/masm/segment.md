---
title: SEGMENTO | Microsoft Docs
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
ms.openlocfilehash: f5defce11b611f23b67e5e44ac1b9d406f73c0ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210424"
---
# <a name="segment"></a>SEGMENT
Define un segmento de programa llamado *nombre* tener atributos de segmento  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>Parámetros  
 *align*  
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
  
 *combine*  
 **PÚBLICA**, **pila**, **común**, **memoria**, **en**<em>dirección</em>, **Privada**  
  
 *Use*  
 **USE16**, **USE32**, **SIN FORMATO**  
  
 `characteristics`  
 **INFORMACIÓN**, **leer**, **escribir**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, y **descartar**  
  
 Estos solo se admiten para COFF y corresponden a las características de la sección COFF de nombre similar (por ejemplo, **SHARED** corresponde a IMAGE_SCN_MEM_SHARED). LECTURA establece la marca IMAGE_SCN_MEM_READ. La marca de solo lectura obsoleta provocó la sección Borrar la marca IMG_SCN_MEM_WRITE. Si cualquier `characteristics` están configurados, no se usan las características de forma predeterminada y solo las marcas especificado por el programador están en vigor.  
  
 `ALIAS(` `string` `)`  
 Esta cadena se usa como el nombre de sección en el objeto COFF emitido.  Crea varias secciones con el mismo nombre externo, con distintos nombres de segmento MASM.  
  
 No es compatible con **/omf**.  
  
 `class`  
 Designa cómo segmentos deben combinarse y ordenados en el archivo de ensamblado. Los valores típicos son, `'DATA'`, `'CODE'`, `'CONST'` y `'STACK'`  
  
## <a name="remarks"></a>Comentarios  
 Para `ALIGN(n)`, `n` puede ser cualquier potencia de 2 desde 1 hasta 8192; no se admite con **/omf**.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)