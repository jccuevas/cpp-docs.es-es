---
title: "SEGMENT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEGMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SEGMENT directive"
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# SEGMENT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define un segmento de programa llamado *name* que tiene atributos de segmento  
  
## Sintaxis  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### Parámetros  
 *alinear*  
 El intervalo de direcciones de memoria de que una dirección inicial para el segmento puede seleccionar.  El tipo de alineación puede ser:  
  
|tipo alinear|Iniciar la dirección|  
|------------------|--------------------------|  
|**BYTE**|dirección de byte disponible siguiente.|  
|**WORD**|dirección de palabra disponible siguiente \(2 bytes por palabra\).|  
|**DWORD**|dirección de doble palabra disponible siguiente \(4 bytes por la doble palabra\).|  
|**PÁG**|Dirección disponible siguiente de párrafo \(16 bytes por párrafo\).|  
|**PÁGINA**|Dirección de página disponible siguiente \(256 bytes por página\).|  
|**Alinear**\(n\)|*Enésimo*dirección de byte disponible siguiente.  Vea la sección comentarios para obtener más información.|  
  
 si este parámetro no se especifica, **PÁG** se utiliza de forma predeterminada.  
  
 *combine*  
 **PÚBLICO**, **PILA**, **Común**, **Memoria**,*dirección de***ON**, **Privado**  
  
 *uso*  
 **USE16**, **USE32**, **Plana**  
  
 `characteristics`  
 **Informacin**, **LECTURA**, **ESCRIBIR**, **EJECUTAR**, **Compartido**, **NOPAGE**, **NOCACHE**, y **Descartar**  
  
 Se admiten para COFF sólo y corresponden a las características de la sección COFF de nombre similar \(por ejemplo, **Compartido** corresponde a IMAGE\_SCN\_MEM\_SHARED\).  La LECTURA establece la marca de IMAGE\_SCN\_MEM\_READ.  El marcador obsoleto READONLY hizo que la sección borrara el indicador de IMG\_SCN\_MEM\_WRITE.  Si se establece en un `characteristics` , las características predeterminadas no se utilicen y sólo los marcadores programador\-especificados están en vigor.  
  
 `ALIAS(` `string` `)`  
 Esta cadena se usa como nombre de la sección del objeto emitido COFF.  Crea varias secciones con el mismo nombre externo, con los nombres de segmento distintos de MASM.  
  
 No compatible con **\/omf**.  
  
 `class`  
 Elija cómo los segmentos deben combinarse y ordenar en el archivo ensamblado.  Los valores habituales son, `'DATA'`, `'CODE'`, `'CONST'` y `'STACK'`  
  
## Comentarios  
 Para `ALIGN(``n``)`, `n` puede ser cualquier eficacia de las 2 de 1 a 8192; no compatible con **\/omf**.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)