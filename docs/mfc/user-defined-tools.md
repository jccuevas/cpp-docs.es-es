---
title: Herramientas definidas por el usuario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8e161ac82a6df238079782768ee44e7bdf359cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425086"
---
# <a name="user-defined-tools"></a>Herramientas definidas por el usuario

MFC admite herramientas definidas por el usuario. Una herramienta definido por el usuario es un comando especial que se ejecuta un programa externo, especificado por el usuario. Puede usar el proceso de personalización para administrar herramientas definidas por el usuario. Sin embargo, no se puede utilizar este proceso si no se deriva el objeto de aplicación [CWinAppEx (clase)](../mfc/reference/cwinappex-class.md). Para obtener más información sobre la personalización, consulte [personalización de MFC](../mfc/customization-for-mfc.md).

Si habilitó la compatibilidad con herramientas definidas por el usuario, el cuadro de diálogo de personalización incluye automáticamente el **herramientas** ficha. La siguiente ilustración muestra el **herramientas** página.

![Pestaña herramientas en el cuadro de diálogo Personalizar](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab") ficha de herramientas del cuadro de diálogo de personalización

## <a name="enabling-user-defined-tools-support"></a>Compatibilidad con herramientas de habilitación definido por el usuario

Para habilitar las herramientas definidas por el usuario en una aplicación, llame a [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Sin embargo, primero debe definir varias constantes en los archivos de recursos de la aplicación para usar como parámetros para esta llamada.

En el editor de recursos, crear un comando ficticio que usa un identificador de comando adecuado. En el ejemplo siguiente, se usa `ID_TOOLS_ENTRY` como el identificador de comando. Este identificador de comando marca una ubicación en los menús de uno o más donde insertará el marco de trabajo a las herramientas definidas por el usuario.

Debe apartar algunos identificadores consecutivos en la tabla de cadenas que representan las herramientas definidas por el usuario. El número de cadenas que se reservan es igual que el número máximo de las herramientas de usuario que los usuarios pueden definir. En el ejemplo siguiente, se denominan `ID_USER_TOOL1` a través de `ID_USER_TOOL10`.

Puede ofrecer sugerencias a los usuarios para ayudarles a seleccionar directorios y los argumentos para los programas externos que se llamará como herramientas. Para ello, cree dos menús emergentes en el editor de recursos. En el ejemplo siguiente se denominan `IDR_MENU_ARGS` y `IDR_MENU_DIRS`. Para cada comando en estos menús, defina una cadena en la tabla de cadenas de la aplicación. El identificador de recurso de la cadena debe ser igual al identificador de comando.

También puede crear una clase derivada de [CUserTool (clase)](../mfc/reference/cusertool-class.md) para reemplazar la implementación predeterminada. Para ello, pase la información en tiempo de ejecución de la clase derivada como cuarto parámetro en CWinAppEx::EnableUserTools, en lugar de RUNTIME_CLASS ([CUserTool (clase)](../mfc/reference/cusertool-class.md)).

Después de definir las constantes correspondientes, llame a [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) para habilitar herramientas definidas por el usuario.

La siguiente llamada de método muestra cómo usar estas constantes:

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

En este ejemplo, la ficha herramientas se incluirán en el **personalización** cuadro de diálogo. El marco de trabajo reemplazará cualquier comando que coincida con el identificador de comando `ID_TOOLS_ENTRY` en ningún menú con el conjunto de herramientas de actualmente definida por el usuario cada vez que un usuario abre ese menú. Los identificadores de comando `ID_USER_TOOL1` a través de `ID_USER_TOOL10` están reservados para uso de herramientas definidas por el usuario. La clase [CUserTool (clase)](../mfc/reference/cusertool-class.md) controla las llamadas a las herramientas de usuario. La pestaña de la herramienta de la **personalización** cuadro de diálogo proporciona botones a la derecha de los campos de entrada de argumento y el directorio para tener acceso a los menús **IDR_MENU_ARGS** y **IDR_MENU_DIRS**. Cuando un usuario selecciona un comando de uno de estos menús, el marco de trabajo anexa al cuadro de texto adecuado la cadena que tiene el identificador de recurso igual que el identificador de comando.

### <a name="including-predefined-tools"></a>Incluye herramientas predefinidas

Si desea predefinir algunas herramientas en el inicio de la aplicación, debe invalidar el [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) método de la ventana principal de la aplicación. En ese método, debe realizar los pasos siguientes.

##### <a name="to-add-new-tools-in-loadframe"></a>Para agregar nuevas herramientas de LoadFrame

1. Obtener un puntero a la [CUserToolsManager (clase)](../mfc/reference/cusertoolsmanager-class.md) objeto mediante una llamada a [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).

1. Para cada herramienta que desea crear, llamar a [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Este método devuelve un puntero a un [CUserTool (clase)](../mfc/reference/cusertool-class.md) de objetos y la herramienta de usuario recién creado se agrega a la colección interna de herramientas. Si ha proporcionado la información en tiempo de ejecución de una clase derivada de [CUserTool (clase)](../mfc/reference/cusertool-class.md) como cuarto parámetro del [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) se crear instancias y devolverá una instancia de esa clase en su lugar.

1. Para cada herramienta, establezca la etiqueta de texto estableciendo `CUserTool::m_strLabel` y establezca su comando mediante una llamada a `CUserTool::SetCommand`. La implementación predeterminada de [CUserTool (clase)](../mfc/reference/cusertool-class.md) recupera automáticamente los iconos disponibles desde el programa que se especifica en la llamada a `SetCommand`.

## <a name="see-also"></a>Vea también

[Personalización de MFC](../mfc/customization-for-mfc.md)<br/>
[CUserTool (clase)](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager (clase)](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx (clase)](../mfc/reference/cwinappex-class.md)




