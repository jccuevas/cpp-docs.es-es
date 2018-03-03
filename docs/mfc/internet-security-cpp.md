---
title: Seguridad de Internet (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a44e528e871d784c432730799c44ac91af465be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="internet-security-c"></a>Seguridad de Internet (C++)
Seguridad de código es un problema grave para desarrolladores como para los usuarios de aplicaciones de Internet. Puede poner en peligro: código malintencionado, el código que se ha alterado y código sitios desconocidos o que los autores.  
  
 Hay dos enfoques básicos para la seguridad al desarrollar para Internet. El primero se denomina "espacio aislado". En este enfoque, una aplicación está restringida a un determinado conjunto de API y excluida que potencialmente peligroso como la E/S de archivo en un programa podría destruir los datos en el equipo del usuario. El segundo se implementa mediante firmas digitales. Este enfoque se conoce como "precinto" para Internet. Código se comprueba y firma mediante tecnología de clave pública y clave privada. Antes de ejecuta el código, su firma digital se comprueba para asegurarse de que el código procede de un origen autenticado conocido y que el código no se ha modificado desde que se firmó.  
  
 En el primer caso, confía en que la aplicación no realizará ningún daño y se confía en el origen de la aplicación. En el segundo, las firmas digitales se usan para comprobar la autenticidad. La firma digital es un estándar del sector que se usa para identificar y proporcionar detalles sobre el publicador del código. Su tecnología se basa en estándares, incluidos RSA y X.509. Los exploradores suelen permiten a los usuarios elegir si desean descargar y ejecutar código de origen desconocido.  
  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

