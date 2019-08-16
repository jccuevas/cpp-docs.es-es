---
title: Cómo el Control de cuentas de usuario (UAC) afecta a la aplicación
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 8c283e86a71092bb510892b6361f3d0fddc2abb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510141"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Cómo el Control de cuentas de usuario (UAC) afecta a la aplicación

El Control de cuentas de usuario (UAC) es una característica de Windows Vista para limitar los privilegios de las cuentas de usuario. Puede encontrar información detallada sobre UAC en estos sitios:

- [Prácticas recomendadas para desarrolladores e instrucciones para aplicaciones en un entorno con privilegios mínimos](/windows/win32/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Compilar proyectos después de habilitar UAC

Si compila un proyecto de Visual C++ Studio en Windows Vista con UAC deshabilitado y posteriormente habilita UAC, debe limpiar y recompilar el proyecto para que funcione correctamente.

## <a name="applications-that-require-administrative-privileges"></a>Aplicaciones que requieren privilegios de administrador

De forma predeterminada, el C++ vinculador visual inserta un fragmento de UAC en el manifiesto de una aplicación con un nivel de `asInvoker`ejecución de. Si su aplicación exige privilegios de administrador para funcionar correctamente (por ejemplo, si modifica el nodo HKLM del Registro o si escribe en áreas protegidas del disco, como el directorio de Windows), deberá modificar su aplicación.

La primera opción consiste en modificar el fragmento de UAC del manifiesto para cambiar el nivel de ejecución a *requireAdministrator*. A continuación, la aplicación pedirá al usuario credenciales administrativas antes de ejecutarse. Para obtener información acerca de cómo hacerlo, consulte [/manifestuac (insertar información de UAC en el manifiesto)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

La segunda opción es no incrustar un fragmento del UAC en el manifiesto especificando la opción del vinculador `/MANIFESTUAC:NO`. En este caso, su aplicación se ejecutará en modo virtualizado. Cualquier modificación que haga en el Registro o en el sistema de archivos no permanecerá después de que su aplicación haya finalizado.

El diagrama de flujo siguiente describe cómo se ejecutará su aplicación en función de si el UAC está habilitado y si la aplicación tiene un manifiesto del UAC:

![Comportamiento del cargador de Windows](media/uacflowchart.png "Comportamiento del cargador de Windows")

## <a name="see-also"></a>Vea también

[Procedimientos recomendados para la seguridad](security-best-practices-for-cpp.md)
