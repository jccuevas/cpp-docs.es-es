---
title: /MANIFESTUAC (Incrustar información de UAC en el manifiesto)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 8ae9d18bb0fe2172886ef24250d53cf76851bbba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420432"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Incrustar información de UAC en el manifiesto)

Especifica si la información de Control de cuentas de usuario (UAC) debe incrustarse en el manifiesto del programa.

## <a name="syntax"></a>Sintaxis

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>Parámetros

*fragment*<br/>
Una cadena que contiene los valores de `level` y `uiAccess`. Para obtener más información, vea la sección Comentarios más adelante en este tema.

*_level*<br/>
Uno de *asInvoker*, *highestAvailable*, o *requireAdministrator*. El valor predeterminado es asInvoker. Para obtener más información, vea la sección Comentarios más adelante en este tema.

*_uiAccess*<br/>
**True** si desea que la aplicación para omitir los niveles de protección de interfaz de usuario e impulsar la entrada a las ventanas de nivel de permisos superior en el escritorio; de lo contrario, **false**. El valor predeterminado es **false**. Establecido en **true** solo para las aplicaciones de accesibilidad de interfaz de usuario.

## <a name="remarks"></a>Comentarios

Si especifica varias opciones /MANIFESTUAC en la línea de comandos, tendrá prioridad la última que escriba.

Las opciones de /MANIFESTUAC:level son las siguientes:

- `asInvoker`: La aplicación se ejecutará con los mismos permisos que el proceso que fue iniciado. La aplicación se puede elevar a un nivel de permisos superior seleccionando **ejecutar como administrador**.

- highestAvailable: La aplicación se ejecutará con el mayor nivel de permiso que lo hace. Si el usuario que inicia la aplicación es miembro del grupo Administradores, esta opción es igual que requireAdministrator. Si el máximo nivel de permisos disponible es superior al nivel del proceso de apertura, el sistema solicitará las credenciales.

- requireAdministrator: La aplicación se ejecutará con permisos de administrador. El usuario que inicia la aplicación debe ser miembro del grupo Administradores. Si el proceso de apertura no se está ejecutando con permisos administrativos, el sistema solicitará las credenciales.

El nivel y los valores de uiAccess se pueden especificar en un solo paso mediante la opción /MANIFESTUAC:fragmento. El fragmento deben tener el formato siguiente:

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **archivo de manifiesto** página de propiedades.

1. Modificar el **habilitar el Control de cuentas de usuario (UAC)**, **nivel de ejecución de UAC**, y **Omitir protección de la interfaz de usuario de UAC** propiedades.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
