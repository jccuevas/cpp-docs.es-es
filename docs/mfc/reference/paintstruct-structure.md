---
title: "PAINTSTRUCT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PAINTSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PAINTSTRUCT (estructura)"
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PAINTSTRUCT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `PAINTSTRUCT` contiene información que se puede utilizar para pintar el área cliente de una ventana.  
  
## Sintaxis  
  
```  
  
      typedef struct tagPAINTSTRUCT {  
   HDC hdc;  
   BOOL fErase;  
   RECT rcPaint;  
   BOOL fRestore;  
   BOOL fIncUpdate;  
   BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### Parámetros  
 *hdc*  
 Identifica el contexto de presentación que se utilizará para pintar.  
  
 *fErase*  
 Especifica si el fondo necesita volver a dibujar.  No es 0 si la aplicación actualizar el fondo.  La aplicación es responsable de dibujar el fondo si una clase de ventana de Windows se crea sin un pincel del fondo \(vea la descripción del miembro de **hbrBackground** de la estructura de [Clase WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]\).  
  
 *rcPaint*  
 Especifica las esquinas superior izquierda e inferior derecha del rectángulo en el que se solicita el dibujo.  
  
 *fRestore*  
 Miembro reservado.  Se utiliza internamente por Windows.  
  
 *fIncUpdate*  
 Miembro reservado.  Se utiliza internamente por Windows.  
  
 *rgbReserved \[16\]*  
 Miembro reservado.  Un bloque de memoria reservado utilizado internamente por Windows.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)