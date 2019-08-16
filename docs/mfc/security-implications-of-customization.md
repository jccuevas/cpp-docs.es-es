---
title: Implicaciones de seguridad de la personalización
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 9164983a6634e069195f3498bea56b595a2a2381
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308477"
---
# <a name="security-implications-of-customization"></a>Implicaciones de seguridad de la personalización

En este tema se describe una vulnerabilidad de seguridad potencial en MFC.

## <a name="potential-security-weakness"></a>Vulnerabilidad de seguridad potencial

MFC permite al usuario personalizar la apariencia de una interfaz de usuario de la aplicación, por ejemplo, la apariencia de botones e iconos. MFC también es compatible con herramientas definidas por el usuario, que permiten al usuario ejecutar comandos de shell. Una vulnerabilidad de seguridad se produce porque la configuración personalizada de la aplicación se guarda en el perfil de usuario en el registro. Cualquier persona que puede tener acceso al registro puede editar estos valores y cambiar la apariencia de la aplicación o el comportamiento. Por ejemplo, un administrador en el equipo podría suplantar a un usuario haciendo que la aplicación del usuario ejecutar programas arbitrarios (incluso en un recurso compartido de red).

## <a name="workarounds"></a>Soluciones

Se recomienda cualquiera de estas tres formas de cerrar las vulnerabilidades en el registro:

- Cifrar los datos que se almacenan allí

- Store los datos en un archivo seguro en lugar de en el registro.

   Para llevar a cabo cualquiera de estas dos primeras maneras, derive una clase de [CSettingsStore Class](../mfc/reference/csettingsstore-class.md) e invalidar sus métodos para implementar el cifrado o almacenamiento fuera del registro.

- También puede deshabilitar las personalizaciones en la aplicación.

## <a name="see-also"></a>Vea también

[Personalización de MFC](../mfc/customization-for-mfc.md)
