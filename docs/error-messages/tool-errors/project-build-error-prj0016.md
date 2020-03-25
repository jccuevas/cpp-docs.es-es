---
title: Error PRJ0016 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 0cab1e35a36ab78426923d60acafb5cdf2942469
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192749"
---
# <a name="project-build-error-prj0016"></a>Error PRJ0016 al compilar el proyecto

La configuración de seguridad del usuario impide que se cree el proceso. Esta configuración es necesaria para la compilación.

Ha iniciado sesión como un usuario que no tiene permisos para crear procesos mediante un proceso. Debe cambiar los niveles de permisos de esta cuenta de usuario o ponerse en contacto con el administrador de la cuenta.

Este error también puede producirse si se establece la siguiente clave del registro:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Para resolver este error, elimine la clave RestrictRun. Si se necesita esta clave del registro, anexe **vcspawn. exe** a la lista de entradas de la clave.

Otra causa de este error es que la configuración de la Directiva no incluye VCSpawn. exe en la clave del registro HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun como programa de ventana permitido para esta cuenta de usuario.

Para obtener más información, vea el tema que trata la [configuración de directivas del sistema](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings), en la sección sobre la ejecución de solo aplicaciones permitidas de Windows.
