---
title: "Ejecutar como miembro del grupo de usuarios | Microsoft Docs"
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
  - "PRJ0050"
  - "VCD0047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Usuarios (grupo) [C++]"
  - "seguridad [C++], grupo de usuarios"
  - "cuentas de Windows [C++]"
  - "usuarios no administradores [C++]"
  - "cuentas de usuario [C++]"
  - "administrador (no ejecutar como) [C++]"
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
caps.latest.revision: 17
caps.handback.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Ejecutar como miembro del grupo de usuarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo configurar las cuentas de usuario de Windows como un miembro del grupo Usuarios \(opuesto al grupo Administradores\) aumenta la seguridad reduciendo las posibilidades de resultar infectado por código malintencionado.  
  
## Riesgos de seguridad  
 Ejecutar como un administrador hace al sistema vulnerable a varios tipos de ataques a la seguridad, como "caballos de Troya" y "saturaciones del búfer". Simplemente visitar un sitio de Internet como administrador puede dañar el sistema, ya que el código malintencionado que se descarga de un sitio de Internet puede atacar al equipo.  Si el ataque llega a ser efectivo, hereda sus permisos de administrador y puede realizar a continuación acciones como eliminar todos los archivos, reformatear la unidad de disco duro y crear nuevas cuentas de usuario con acceso administrativo.  
  
## Grupos de usuarios que no son administradores  
 Las cuentas de usuario de Windows que utilizan normalmente los desarrolladores se deben agregar a los grupos Usuarios o Usuarios avanzados.  Los desarrolladores también se deben agregar al grupo Depuración.  Ser integrante del grupo Usuarios permite realizar tareas rutinarias, incluida la ejecución de programas y la visita a sitios de Internet sin exponer el equipo a riesgos innecesarios.  Como miembro del grupo Usuarios avanzados, también puede realizar tareas como la instalación de aplicaciones, instalación de impresoras y la mayoría de las operaciones del Panel de control.  Si debe realizar tareas administrativas como actualizar el sistema operativo o configurar parámetros del sistema, tendrá que iniciar una sesión con una cuenta de administrador durante el tiempo que realice las tareas administrativas.  De modo alternativo, el comando **runas** de Windows se puede utilizar para iniciar aplicaciones específicas con acceso administrativo.  
  
## Exponer a los clientes a riesgos de seguridad  
 No ser integrante del grupo Administradores es particularmente importante para los desarrolladores porque, además de proteger los equipos de desarrollo, evita que éstos escriban sin querer código que requiera que los clientes se unan al grupo Administradores para ejecutar las aplicaciones que desarrolla.  Si durante el desarrollo se introduce código que requiere acceso de administrador, fallará en tiempo de ejecución, alertándole del hecho de que la aplicación ahora requiere que los clientes ejecuten como Administradores.  
  
## Código que requiere privilegios de administrador  
 Algún código requiere el acceso de Administrador para ejecutarse.  Si es posible, se deberían buscar alternativas a este código.  Ejemplos de operaciones de código que requieren el acceso de Administrador son:  
  
-   Escribir en las áreas protegidas del sistema de archivos, por ejemplo los directorios Windows o Archivos de programa  
  
-   Escribir en las áreas protegidas del Registro, por ejemplo HKEY\_LOCAL\_MACHINE  
  
-   Instalar ensamblados en la Caché global de ensamblados \(GAC\)  
  
 Generalmente, estas acciones se deberían restringir a los programas de instalación de aplicaciones.  Esto permite a los usuarios utilizar el estado de administrador sólo temporalmente.  
  
## Depuración  
 Puede depurar cualquier aplicación que se inicie dentro de Visual Studio \(nativa y no administrada\) no como administrador, volviéndose parte del grupo Depuración.  Esto incluye la capacidad de asociar a una aplicación en ejecución mediante el comando Asociar al proceso.  Sin embargo, es necesario formar parte del grupo Administrador para depurar aplicaciones nativas o administradas iniciadas por un usuario diferente.  
  
## Vea también  
 [Procedimientos recomendados](../top/security-best-practices-for-cpp.md)