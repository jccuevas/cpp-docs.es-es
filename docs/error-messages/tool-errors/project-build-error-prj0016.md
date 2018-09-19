---
title: Error PRJ0016 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6604bc0bf27b3d0192f602c4df88e5f01e4a161
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135963"
---
# <a name="project-build-error-prj0016"></a>Error PRJ0016 al compilar el proyecto

Configuración de seguridad del usuario impide que el proceso que se está creando. Esta configuración es necesaria para la compilación.

Se registran en como un usuario que no tiene permisos para crear procesos mediante un proceso. Debe cambiar los niveles de permisos para esta cuenta de usuario, o póngase en contacto con el Administrador de cuentas.

Este error puede producirse también si se establece la clave del registro siguiente:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Para resolver este error, elimine la clave RestrictRun. Si se necesita esta clave del registro, anexar **vcspawn.exe** a la lista de entradas de la clave.

Otra causa de este error es que la configuración de directivas no incluye VCSpawn.exe en la clave del Registro HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun como programa de ventana permitido para esta cuenta de usuario.

Para obtener más información, consulte:

- Artículo de Knowledge Base 324153, que está disponible en [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).

- [Cumplir con la configuración de directiva de sistema](https://msdn.microsoft.com/library/aa372139), la sección en "Ejecutar sólo aplicaciones permitidas de Windows".