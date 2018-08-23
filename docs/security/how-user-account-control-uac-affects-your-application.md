---
title: Cómo el Control de cuentas de usuario (UAC) afecta a la aplicación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23266ca4b4d32146ed8627c6ce3ab1cc878d59cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600657"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Cómo el Control de cuentas de usuario (UAC) afecta a la aplicación
El Control de cuentas de usuario (UAC) es una característica de Windows Vista para limitar los privilegios de las cuentas de usuario. Puede encontrar información detallada sobre UAC en estos sitios:  
  
-   [Guía paso a paso de Control de cuentas de usuario de Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=53781)  
  
-   [Developer Best Practices and Guidelines for Applications in a Least Privileged Environment](http://go.microsoft.com/fwlink/p/?linkid=82444)  
  
-   [Descripción y configuración de Control de cuentas de usuario en Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>Compilar proyectos después de habilitar UAC  
 Si compila un proyecto de Visual C++ en Windows Vista con UAC deshabilitado, y posteriormente lo habilita, deberá limpiar y recompilar el proyecto para que funcione correctamente.  
  
## <a name="applications-that-require-administrative-privileges"></a>Aplicaciones que requieren privilegios de administrador  
 De forma predeterminada, el vinculador de Visual C++ incrusta un fragmento del UAC en el manifiesto de una aplicación con un nivel de ejecución de `asInvoker`. Si su aplicación exige privilegios de administrador para funcionar correctamente (por ejemplo, si modifica el nodo HKLM del Registro o si escribe en áreas protegidas del disco, como el directorio de Windows), deberá modificar su aplicación.  
  
 La primera opción es modificar el fragmento del UAC del manifiesto para cambiar el nivel de ejecución a *requireAdministrator*. A continuación, la aplicación pedirá al usuario credenciales administrativas antes de ejecutarse. Para obtener información acerca de cómo hacerlo, consulte [/MANIFESTUAC (insertar información de UAC en el manifiesto)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 La segunda opción es no incrustar un fragmento del UAC en el manifiesto especificando la opción del vinculador `/MANIFESTUAC:NO`. En este caso, su aplicación se ejecutará en modo virtualizado. Cualquier modificación que haga en el Registro o en el sistema de archivos no permanecerá después de que su aplicación haya finalizado.  
  
 El diagrama de flujo siguiente describe cómo se ejecutará su aplicación en función de si el UAC está habilitado y si la aplicación tiene un manifiesto del UAC:  
  
 ![Comportamiento del cargador de Windows Vista](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos recomendados para la seguridad](security-best-practices-for-cpp.md)