---
title: "Funci&#243;n de devoluci&#243;n de llamada para CDC::GrayString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Callback Function for CDC::GrayString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de devolución de llamada, para CDC::GrayString"
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Funci&#243;n de devoluci&#243;n de llamada para CDC::GrayString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

*OutputFunc* es un marcador de posición para el nombre de función de devolución de llamada aplicación\- proporcionado.  
  
## Sintaxis  
  
```  
  
      BOOL CALLBACK EXPORT OutputFunc(   
   HDC hDC,   
   LPARAM lpData,   
   int nCount    
);  
```  
  
#### Parámetros  
 `hDC`  
 Identifica un contexto de dispositivo de memoria con un mapa de bits por lo menos width y height especificados por `nWidth` y `nHeight` a `GrayString`.  
  
 `lpData`  
 Apunta a la cadena de caracteres que se va a dibujar.  
  
 `nCount`  
 Especifica el número de caracteres para generar.  
  
## Valor devuelto  
 El valor devuelto de la función de devolución de llamada debe ser **VERDADERO** para indicar; si no es **FALSE**.  
  
## Comentarios  
 La función de devolución de llamada \(*OutputFunc*\) debe dibujar una imagen en relación con las coordenadas \(0,0\) en lugar de \(*x*, *y\)*.  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GrayString](../Topic/CDC::GrayString.md)