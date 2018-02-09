---
title: Limitaciones de CImage con sistemas operativos anteriores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CImage
dev_langs:
- C++
helpviewer_keywords:
- CImage class [MFC], limitations
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27046704975bf8f5e28f12acbfa72e860660fdbd
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2018
---
# <a name="cimage-limitations-with-earlier-operating-systems"></a>Limitaciones de CImage con sistemas operativos anteriores
Muchas `CImage` funciones solo funcionan con las versiones más recientes de Windows: Windows 95 o Windows 98 o Windows NT 4.0 o Windows 2000. En este artículo se describe las limitaciones de versión de ciertos métodos.  
  
 [CImage::PlgBlt](../atl-mfc-shared/reference/cimage-class.md#plgblt) y [CImage:: MaskBlt](../atl-mfc-shared/reference/cimage-class.md#maskblt) funcionan con solo Windows NT 4.0 o posterior. No funcionará en aplicaciones que se ejecutan en Windows 95 ó 98 o versiones posteriores.  
  
 [CImage::AlphaBlend](../atl-mfc-shared/reference/cimage-class.md#alphablend) y [CImage:: TransparentBlt](../atl-mfc-shared/reference/cimage-class.md#transparentblt) funcionan con sólo Windows 2000 o posterior y Windows 98 o posterior, ya que debe vincular con msimg32.lib para utilizar estos métodos. (Esta biblioteca está disponible sólo para las aplicaciones que ejecutan Windows 2000 o posterior y Windows 98 o posterior.)  
  
 Puede incluir `AlphaBlend` y `TransparentBlt` en una aplicación que se ejecuta en Windows 95 o Windows NT 4.0 sólo si nunca se llaman a estos métodos. Si la aplicación incluye estos métodos, y debe ejecutarse en sistemas operativos anteriores, debe usar el vinculador [/DELAYLOAD](../build/reference/delayload-delay-load-import.md) para retrasar la carga de msimg32.lib. Siempre y cuando la aplicación no llama a uno de estos métodos mientras se ejecuta en Windows NT 4.0 o Windows 95, no intentará cargar msimg32.lib. Se puede comprobar la compatibilidad de transparencia está disponible con la `CImage::IsTransparencySupported` método.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 Para compilar una aplicación que llama a estos métodos, inserte un # _WIN32_WINNT instrucción define antes de #including system encabezados, que indica que la versión de Windows es igual o mayor que 5.0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 Si no necesita la aplicación para que se ejecute en un sistema operativo anterior a Windows 2000 o Windows 98, puede vincular a msimg32.lib directamente sin usar **/DELAYLOAD**.  
  
 [CImage::Draw](../atl-mfc-shared/reference/cimage-class.md#draw) tiene un comportamiento diferente cuando se usa con Windows 2000 y Windows 98, que lo hace con Windows NT 4.0 o Windows 95.  
  
 Si se compila la aplicación con el conjunto de _WIN32_WINNT en un valor menor que 0 x 0500, **dibujar** trabajo, pero no se podrá controlar la transparencia automáticamente en sistemas que ejecutan Windows 2000 y Windows 98 y versiones posteriores.  
  
 Si se compilan la aplicación con _WIN32_WINNT establecido en 0 x 0500 o mayor, **dibujar** podrá controlar la transparencia automáticamente en sistemas que ejecutan Windows 2000 o Windows 98 y versiones posteriores. También funcionará, pero sin compatibilidad con transparencia, con Windows NT 4.0 y Windows 95; Sin embargo, debe usar **/DELAYLOAD** para retrasar la carga de msimg32. LIB, tal y como se describió anteriormente para `AlphaBlend` y `TransparentBlt`.  
  
## <a name="see-also"></a>Vea también  
 [CImage (clase)](../atl-mfc-shared/reference/cimage-class.md)
