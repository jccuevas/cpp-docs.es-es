---
title: Teclas de aceleración (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362392"
---
# <a name="accelerator-keys-c"></a>Teclas de aceleración (C++)

## <a name="predefined-accelerator-keys"></a>Teclas de aceleración predefinidas

Hay una serie de teclas de aceleración predefinidas que pueden formar parte de un proyecto de aplicación de Windows. Algunas de estas teclas virtuales se destinan al entorno de Windows. Otras admiten explorador o aplicaciones Unicode. Puede usar una de estas teclas en cualquier acelerador.

|Key|Descripción|
|---------|-----------------|
|VK_ACCEPT|(IME) Aceptar|
|VK_BROWSER_BACK|(Windows) Explorador, **volver** clave|
|VK_BROWSER_FAVORITES|(Windows) Explorador, **favoritos** clave|
|VK_BROWSER_FORWARD|(Windows) Explorador, **reenviar** clave|
|VK_BROWSER_HOME|(Windows) Explorador, **iniciar** y **inicio** clave|
|VK_BROWSER_REFRESH|(Windows) Explorador, **actualizar** clave|
|VK_BROWSER_SEARCH|(Windows) Explorador, **búsqueda** clave|
|VK_BROWSER_STOP|(Windows) Explorador, **detener** clave|
|VK_CONVERT|Convert (IME)|
|VK_FINAL|Modo final (IME)|
|VK_HANGUEL|(IME) Modo Hanguel (se mantiene por compatibilidad, use VK_HANGUL)|
|VK_HANGUL|(IME) Modo hangul|
|VK_HANJA|(IME) Modo hanja|
|VK_JUNJA|(IME) Modo Junja|
|VK_KANA|(IME) Modo kana|
|VK_KANJI|(IME) Modo Kanji|
|VK_LAUNCH_APP1|(Windows) **Iniciar aplicación 1** clave|
|VK_LAUNCH_APP2|(Windows) **Iniciar aplicación 2** clave|
|VK_LAUNCH_MAIL|(Windows) **Iniciar correo electrónico** clave|
|VK_LAUNCH_MEDIA_SELECT|(Windows) **Seleccionar medio** clave|
|VK_LCONTROL|**Ctrl izquierda** clave|
|VK_LMENU|**Menú de la izquierda** clave|
|VK_LSHIFT|**Desplazamiento a la izquierda** clave|
|VK_MEDIA_NEXT_TRACK|(Windows) **Pista siguiente** clave|
|VK_MEDIA_PLAY_PAUSE|(Windows) **Reproducir/pausar medio** clave|
|VK_MEDIA_PREV_TRACK|(Windows) **Pista anterior** clave|
|VK_MEDIA_STOP|(Windows) **Detener medios** clave|
|VK_MODECHANGE|Solicitud de cambio de modo (IME)|
|VK_NONCONVERT|No conversión (IME)|
|VK_OEM_1|(Windows) Para el teclado estándar de Estados Unidos, la **;:** clave|
|VK_OEM_102|(Windows) La tecla de corchete angular de cierre o la tecla de barra diagonal inversa en el teclado de 102 teclas RT|
|VK_OEM_2|(Windows) ¿Para el teclado estándar de Estados Unidos, la **/?** key|
|VK_OEM_3|(Windows) Para el teclado estándar de Estados Unidos, la **`~** clave|
|VK_OEM_4|(Windows) Para el teclado estándar de Estados Unidos, la **[{** clave|
|VK_OEM_5|(Windows) Para el teclado estándar de Estados Unidos, la **\\ &#124;** clave|
|VK_OEM_6|(Windows) Para el teclado estándar de Estados Unidos, la **]}** clave|
|VK_OEM_7|(Windows) Para el teclado estándar de Estados Unidos, la tecla ' comilla/double-comilla'|
|VK_OEM_COMMA|(Windows) Para cualquier país o región, el **,** clave|
|VK_OEM_MINUS|(Windows) Para cualquier país o región, el **-** clave|
|VK_OEM_PERIOD|(Windows) Para cualquier país o región, el **.** key|
|VK_OEM_PLUS|(Windows) Para cualquier país o región, el **+** clave|
|VK_PACKET|(Windows) Se usa para pasar caracteres Unicode como si fueran pulsaciones de teclas.|
|VK_RCONTROL|**Ctrl derecha** clave|
|VK_RMENU|**Menú derecho** clave|
|VK_RSHIFT|**Desplazamiento a la derecha** clave|
|VK_SLEEP|**Equipo suspendido** clave|
|VK_VOLUME_DOWN|(Windows) **Bajar volumen** clave|
|VK_VOLUME_MUTE|(Windows) **Silenciar volumen** clave|
|VK_VOLUME_UP|(Windows) **Subir volumen** clave|
|VK_XBUTTON1|(Windows) **X1** botón del mouse|
|VK_XBUTTON2|(Windows) **X2** botón del mouse|

## <a name="accelerator-key-association"></a>Acelerador de la asociación de clave

Muchas veces se desea que un elemento de menú y una combinación de teclado ejecuten el mismo comando de programa. Realice esta acción, se asigna el mismo identificador de recurso (Id.) para el elemento de menú y una entrada en la tabla de aceleradores de la aplicación. A continuación, edite el título del elemento de menú para que muestre el nombre del acelerador. Para obtener más información sobre los elementos de menú y las teclas de aceleración, vea [comandos de menú](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de aceleradores](../windows/accelerator-editor.md)<br/>