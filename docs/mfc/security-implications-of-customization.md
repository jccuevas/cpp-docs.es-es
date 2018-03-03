---
title: "Implicaciones de seguridad de personalización | Documentos de Microsoft"
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
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b408b4595e95016323d2b43f1ed51fc6e2e6d244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="security-implications-of-customization"></a>Implicaciones de seguridad de la personalización
Este tema describe una vulnerabilidad de seguridad potencial en MFC.  
  
## <a name="potential-security-weakness"></a>Vulnerabilidad de seguridad potencial  
 MFC permite al usuario personalizar la apariencia de una interfaz de usuario de la aplicación, por ejemplo, el aspecto de botones e iconos. MFC también es compatible con herramientas definidas por el usuario, que permiten al usuario ejecutar comandos de shell. Una vulnerabilidad de seguridad se produce porque la configuración personalizada de la aplicación se guarda en el perfil de usuario en el registro. Cualquier persona que puede tener acceso al registro puede editar estos valores y cambiar la apariencia de la aplicación o el comportamiento. Por ejemplo, un administrador en el equipo podría suplantar a un usuario haciendo que la aplicación del usuario ejecutar programas arbitrarios (incluso desde un recurso compartido de red).  
  
## <a name="workarounds"></a>Soluciones  
 Se recomienda cualquiera de estos tres métodos para cerrar las vulnerabilidades en el registro:  
  
-   Cifrar los datos que se almacenan allí  
  
-   Almacenar los datos en un archivo seguro en lugar de en el registro.  
  
     Para llevar a cabo cualquiera de estas dos formas, derive una clase de [clase CSettingsStore](../mfc/reference/csettingsstore-class.md) e invalidar sus métodos para implementar el cifrado o almacenamiento fuera del registro.  
  
-   También puede deshabilitar las personalizaciones en la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de MFC](../mfc/customization-for-mfc.md)

