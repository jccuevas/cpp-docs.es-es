---
title: Teclas de aceleraciónC++()
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: beb4e878138da3dc2905c86e18fedc658d7ceecf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215155"
---
# <a name="accelerator-keys-c"></a>Teclas de aceleraciónC++()

## <a name="predefined-accelerator-keys"></a>Teclas de aceleración predefinidas

Hay una serie de teclas de aceleración predefinidas que pueden formar parte de un proyecto de aplicación de Windows. Algunas de estas teclas virtuales se destinan al entorno de Windows. Otros admiten aplicaciones de explorador o Unicode. Puede usar una de estas teclas en cualquier acelerador.

|Clave|Descripción|
|---------|-----------------|
|VK_ACCEPT|(IME) Accept|
|VK_BROWSER_BACK|Windows Explorador, tecla **atrás**|
|VK_BROWSER_FAVORITES|Windows Explorador, tecla **Favoritos**|
|VK_BROWSER_FORWARD|Windows Explorador, tecla **adelante**|
|VK_BROWSER_HOME|Windows Explorador, **Start** tecla Inicio **y Inicio**|
|VK_BROWSER_REFRESH|Windows Explorador, clave de **actualización**|
|VK_BROWSER_SEARCH|Windows Explorador, clave de **búsqueda**|
|VK_BROWSER_STOP|Windows Explorador, tecla **detener**|
|VK_CONVERT|(IME) convertir|
|VK_FINAL|(IME) modo final|
|VK_HANGUEL|IME Modo Hanguel (se mantiene por compatibilidad, use VK_HANGUL)|
|VK_HANGUL|IME Modo hangul|
|VK_HANJA|IME Modo hanja|
|VK_JUNJA|IME Modo Junja|
|VK_KANA|IME Modo Kana|
|VK_KANJI|IME Kanji (modo)|
|VK_LAUNCH_APP1|Windows Tecla **Iniciar aplicación 1**|
|VK_LAUNCH_APP2|Windows Tecla **Iniciar aplicación 2**|
|VK_LAUNCH_MAIL|Windows **Iniciar** clave de correo|
|VK_LAUNCH_MEDIA_SELECT|Windows **Seleccionar** clave de medio|
|VK_LCONTROL|Tecla **Ctrl izquierda**|
|VK_LMENU|Tecla de **menú izquierda**|
|VK_LSHIFT|Tecla **MAYÚS izquierda**|
|VK_MEDIA_NEXT_TRACK|Windows Tecla **pista siguiente**|
|VK_MEDIA_PLAY_PAUSE|Windows **Reproducir/pausar tecla multimedia**|
|VK_MEDIA_PREV_TRACK|Windows Tecla de **pista anterior**|
|VK_MEDIA_STOP|Windows **Detener** clave de medio|
|VK_MODECHANGE|Solicitud de cambio de modo (IME)|
|VK_NONCONVERT|(IME) no convertir|
|VK_OEM_1|Windows Para el teclado estándar de Estados Unidos, la tecla **;:**|
|VK_OEM_102|Windows La tecla corchete angular o la tecla de barra diagonal inversa del teclado RT 102-Key|
|VK_OEM_2|Windows Para el teclado estándar de Estados Unidos, el **/?** key|
|VK_OEM_3|Windows Para el teclado estándar de Estados Unidos, la tecla **`~**|
|VK_OEM_4|Windows Para el teclado estándar de Estados Unidos, **[{** clave]|
|VK_OEM_5|Windows Para el teclado estándar de Estados Unidos, la tecla **\\&#124;**|
|VK_OEM_6|Windows Para el teclado estándar de Estados Unidos, la tecla **]}**|
|VK_OEM_7|Windows Para el teclado estándar de Estados Unidos, la tecla ' comilla simple/comilla doble '|
|VK_OEM_COMMA|Windows Para cualquier país o región **, la clave**|
|VK_OEM_MINUS|Windows Para cualquier país o región, la clave **-**|
|VK_OEM_PERIOD|Windows Para cualquier país o región, el **.** key|
|VK_OEM_PLUS|Windows Para cualquier país o región, la clave **+**|
|VK_PACKET|Windows Se usa para pasar caracteres Unicode como si fueran pulsaciones de teclas.|
|VK_RCONTROL|Tecla **Ctrl derecha**|
|VK_RMENU|Tecla de **menú derecha**|
|VK_RSHIFT|Tecla **MAYÚS derecha**|
|VK_SLEEP|Tecla de **suspensión del equipo**|
|VK_VOLUME_DOWN|Windows Tecla **bajar volumen**|
|VK_VOLUME_MUTE|Windows Tecla **silenciar volumen**|
|VK_VOLUME_UP|Windows **Subir clave de volumen**|
|VK_XBUTTON1|Windows **X1** botón del mouse|
|VK_XBUTTON2|Windows Botón del mouse **x2**|

## <a name="accelerator-key-association"></a>Asociación de teclas de aceleración

Muchas veces se desea que un elemento de menú y una combinación de teclado ejecuten el mismo comando de programa. Para realizar esta acción, asigne el mismo identificador de recurso (ID.) al elemento de menú y a una entrada de la tabla de aceleradores de la aplicación. A continuación, edite el título del elemento de menú para que muestre el nombre del acelerador. Para obtener más información sobre los elementos de menú y las teclas de aceleración, vea [comandos de menú](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editor de aceleradores](../windows/accelerator-editor.md)<br/>
