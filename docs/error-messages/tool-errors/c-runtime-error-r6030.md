---
title: Error en tiempo de ejecución de C R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197124"
---
# <a name="c-runtime-error-r6030"></a>Error en tiempo de ejecución de C R6030

CRT no inicializado

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Este problema suele deberse a ciertos programas de software de seguridad o, en raras ocasiones, por un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - El software de seguridad puede tener instrucciones específicas para mitigar este problema. Consulte el sitio web del proveedor de software de seguridad para obtener más información. También puede comprobar si hay versiones actualizadas del software de seguridad o probar un software de seguridad diferente.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce si se usa el tiempo de ejecución de C (CRT), pero no se ejecutó el código de inicio de CRT. Es posible obtener este error si se usa el modificador del enlazador [/entry](../../build/reference/entry-entry-point-symbol.md) para reemplazar la dirección inicial predeterminada, normalmente **mainCRTStartup**, **wmainCRTStartup** para un exe de la consola, **WinMainCRTStartup** o **wWinMainCRTStartup** para un archivo exe de Windows o **_DllMainCRTStartup** para un archivo dll. A menos que se llame a una de las funciones anteriores en el inicio, el tiempo de ejecución de C no se inicializará. Normalmente, se llama a estas funciones de inicio de forma predeterminada al vincular a la biblioteca en tiempo de ejecución de C y utilizar los puntos de entrada **principales**, **wmain**, **WinMain**o **DllMain** normales.

También es posible obtener este error cuando otro programa usa técnicas de inyección de código para interceptar ciertas llamadas a la biblioteca DLL. Algunos programas de seguridad intrusivos usan esta técnica. En las versiones de C++ visual anteriores a visual Studio 2015, se puede usar una biblioteca CRT vinculada estáticamente para solucionar el problema, pero esto no se recomienda por motivos de seguridad y actualizaciones de aplicaciones. La corrección de este problema puede requerir la acción del usuario final.
