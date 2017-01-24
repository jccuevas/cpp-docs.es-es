---
title: "Limitaciones de CImage con sistemas operativos anteriores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImage (clase), limitaciones"
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Limitaciones de CImage con sistemas operativos anteriores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas funciones de `CImage` solo funcionan con versiones más recientes de Windows: Windows 95\/98 ni Windows NT 4.0, o Windows 2000.  En este artículo se describe las limitaciones de la versión de determinados métodos.  
  
 [CImage::PlgBlt](../Topic/CImage::PlgBlt.md) y [CImage::MaskBlt](../Topic/CImage::MaskBlt.md) solo funcionan con Windows NT 4.0 o posterior.  No funcionará en aplicaciones que se ejecutan en Windows 95\/98 o posterior.  
  
 [CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md) y [CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md) solo funcionan con Windows 2000 o posterior y Windows 98 o posterior porque debe vincular con msimg32.lib para utilizar estos métodos. \(Esta biblioteca solo está disponible para las aplicaciones que ejecutan Windows 2000 o posterior y Windows 98 o posterior.\)  
  
 Puede incluir `AlphaBlend` y `TransparentBlt` en una aplicación que se ejecuta en Windows 95 o Windows NT 4.0 únicamente si estos métodos nunca obtienen denominado.  Si la aplicación incluye estos métodos, y debe ejecutarse en sistemas operativos anteriores, debe utilizar [\/delayload](../build/reference/delayload-delay-load-import.md) del vinculador para retrasar la carga de msimg32.lib.  Mientras la aplicación no llame a uno de estos métodos mientras se ejecuta en Windows NT 4.0 o Windows 95, no intentará cargar msimg32.lib.  Puede comprobar si la compatibilidad de transparencia esté disponible mediante el método de `CImage::IsTransparencySupported` .  
  
## Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 Para compilar una aplicación que llama a estos métodos, inserte una instrucción \#define \_WIN32\_WINNT antes de \#including los encabezados de sistema, que indica que la versión de Windows es igual o mayor que 5,0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 Si la aplicación no necesita ejecutarse en un sistema operativo anterior a Windows 2000 o Windows 98, puede vincular directamente a msimg32.lib sin utilizar **\/delayload**.  
  
 [CImage::Draw](../Topic/CImage::Draw.md) se comporta de manera diferente cuando se utiliza con Windows 2000 y Windows 98 que hace con Windows NT 4.0 o Windows 95.  
  
 Si compila la aplicación con \_WIN32\_WINNT establecido en un valor menor que 0x0500, **Dibujar** funcionará, pero no controlará la transparencia automáticamente en sistemas que ejecutan Windows 2000 y Windows 98 y posterior.  
  
 Si compila la aplicación con \_WIN32\_WINNT establecido en 0x0500 o superior, **Dibujar** controlará la transparencia automáticamente en sistemas que ejecutan Windows 2000 o Windows 98 y posterior.  También funcionará, pero sin compatibilidad de transparencia, con Windows NT 4.0 y Windows 95; sin embargo, debe utilizar **\/delayload** para retrasar la carga de msimg32.LIB, como se describe más arriba para `AlphaBlend` y `TransparentBlt`.  
  
## Vea también  
 [CImage Class](../atl-mfc-shared/reference/cimage-class.md)