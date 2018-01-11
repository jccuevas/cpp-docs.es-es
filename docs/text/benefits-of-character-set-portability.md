---
title: "Ventajas de carácter portabilidad de los juegos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 554137352c0a8f7275a051e4026020fce25edbb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-of-character-set-portability"></a>Ventajas de la portabilidad de los juegos de caracteres
Puede beneficiarse del uso de funciones de portabilidad de tiempo de ejecución de C y MFC incluso aunque no piense actualmente a internacionalizar la aplicación:  
  
-   Código portable hace que el código base flexible. Más adelante se puede mover fácilmente a Unicode o MBCS.  
  
-   El uso de Unicode hace que las aplicaciones para Windows 2000 sean más eficaces. Dado que Windows 2000 utiliza Unicode, deben convertirse cadenas no Unicode que se pasan a y desde el sistema operativo, lo que produce la sobrecarga.  
  
-   La utilización de MBCS permite admitir los mercados internacionales en plataformas de Win32 que no sea Windows 2000, como Windows 95 o Windows 98.  
  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Compatibilidad con Unicode](../text/support-for-unicode.md)