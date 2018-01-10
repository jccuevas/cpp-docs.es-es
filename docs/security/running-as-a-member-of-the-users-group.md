---
title: Ejecutar como miembro del grupo de usuarios | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PRJ0050
- VCD0047
dev_langs: C++
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff2a33cd113b631ab6c17cdb02fb29e27d663c1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="running-as-a-member-of-the-users-group"></a>Ejecutar como miembro del grupo de usuarios
Este tema explica cómo configurar las cuentas de usuario de Windows como un miembro del grupo Usuarios (opuesto al grupo Administradores) aumenta la seguridad reduciendo las posibilidades de resultar infectado por código malintencionado.  
  
## <a name="security-risks"></a>Riesgos de seguridad  
 Ejecutar como un administrador hace al sistema vulnerable a varios tipos de ataques a la seguridad, como "caballos de Troya" y "saturaciones del búfer". Simplemente visitar un sitio de Internet como administrador puede dañar el sistema, ya que el código malintencionado que se descarga de un sitio de Internet puede atacar al equipo. Si el ataque llega a ser efectivo, hereda sus permisos de administrador y puede realizar a continuación acciones como eliminar todos los archivos, reformatear la unidad de disco duro y crear nuevas cuentas de usuario con acceso administrativo.  
  
## <a name="non-administrator-user-groups"></a>Grupos de usuarios que no son administradores  
 Las cuentas de usuario de Windows que utilizan normalmente los desarrolladores se deben agregar a los grupos Usuarios o Usuarios avanzados. Los desarrolladores también se deben agregar al grupo Depuración. Ser integrante del grupo Usuarios permite realizar tareas rutinarias, incluida la ejecución de programas y la visita a sitios de Internet sin exponer el equipo a riesgos innecesarios. Como miembro del grupo Usuarios avanzados, también puede realizar tareas como la instalación de aplicaciones, instalación de impresoras y la mayoría de las operaciones del Panel de control. Si debe realizar tareas administrativas como actualizar el sistema operativo o configurar parámetros del sistema, tendrá que iniciar una sesión con una cuenta de administrador durante el tiempo que realice las tareas administrativas. Como alternativa, las ventanas **runas** comando se puede usar para iniciar aplicaciones específicas con acceso administrativo.  
  
## <a name="exposing-customers-to-security-risks"></a>Exponer a los clientes a riesgos de seguridad  
 No ser integrante del grupo Administradores es particularmente importante para los desarrolladores porque, además de proteger los equipos de desarrollo, evita que éstos escriban sin querer código que requiera que los clientes se unan al grupo Administradores para ejecutar las aplicaciones que desarrolla. Si durante el desarrollo se introduce código que requiere acceso de administrador, fallará en tiempo de ejecución, alertándole del hecho de que la aplicación ahora requiere que los clientes ejecuten como Administradores.  
  
## <a name="code-that-requires-administrator-privileges"></a>Código que requiere privilegios de administrador  
 Algún código requiere el acceso de Administrador para ejecutarse. Si es posible, se deberían buscar alternativas a este código. Ejemplos de operaciones de código que requieren el acceso de Administrador son:  
  
-   Escribir en las áreas protegidas del sistema de archivos, por ejemplo los directorios Windows o Archivos de programa  
  
-   Escribir en las áreas protegidas del Registro, por ejemplo HKEY_LOCAL_MACHINE  
  
-   Instalar ensamblados en la Caché global de ensamblados (GAC)  
  
 Generalmente, estas acciones se deberían restringir a los programas de instalación de aplicaciones. Esto permite a los usuarios utilizar el estado de administrador sólo temporalmente.  
  
## <a name="debugging"></a>Depuración  
 Puede depurar cualquier aplicación que se inicie dentro de Visual Studio (nativa y no administrada) no como administrador, volviéndose parte del grupo Depuración. Esto incluye la capacidad de asociar a una aplicación en ejecución mediante el comando Asociar al proceso. Sin embargo, es necesario formar parte del grupo Administrador para depurar aplicaciones nativas o administradas iniciadas por un usuario diferente.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos recomendados para la seguridad](security-best-practices-for-cpp.md)