---
title: Teclas de aceleración (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 1e87d80b8995760eecda34334dab702480bd9669
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232128"
---
# <a name="accelerator-keys-c"></a>Teclas de aceleración (C++)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="predefined-accelerator-keys"></a>Teclas de aceleración predefinidas

Hay una serie de teclas de aceleración predefinidas que pueden formar parte de un proyecto de aplicación de Windows. Algunas de estas teclas virtuales se destinan al entorno de Windows. Otras admiten exploradores o aplicaciones Unicode. Puede usar una de estas teclas en cualquier acelerador.

|Key|Descripción|
|---------|-----------------|
|VK_ACCEPT|Aceptación de IME|
|VK_BROWSER_BACK|Windows: Tecla Atrás del explorador|
|VK_BROWSER_FAVORITES|Windows: Tecla Favoritos del explorador|
|VK_BROWSER_FORWARD|Windows: Tecla adelante del explorador|
|VK_BROWSER_HOME|Windows: Clave e inicio del explorador|
|VK_BROWSER_REFRESH|Windows: Tecla Actualizar del explorador|
|VK_BROWSER_SEARCH|Windows: Tecla búsqueda del explorador|
|VK_BROWSER_STOP|Windows: Tecla Detener del explorador|
|VK_CONVERT|Conversión de IME|
|VK_FINAL|Modo final de IME|
|VK_HANGUEL|Modo Hanguel de IME (se mantiene por compatibilidad; use VK_HANGUL)|
|VK_HANGUL|Modo Hangul de IME|
|VK_HANJA|Modo Hanja de IME|
|VK_JUNJA|Modo Junja de IME|
|VK_KANA|Modo Kana de IME|
|VK_KANJI|Modo Kanji de IME|
|VK_LAUNCH_APP1|Windows: Iniciar aplicación 1 clave|
|VK_LAUNCH_APP2|Windows: Iniciar aplicación 2 clave|
|VK_LAUNCH_MAIL|Windows: Tecla de correo electrónico de inicio|
|VK_LAUNCH_MEDIA_SELECT|Windows: Tecla Seleccionar medio|
|VK_LCONTROL|Tecla CONTROL izquierda|
|VK_LMENU|Tecla MENÚ izquierda|
|VK_LSHIFT|Tecla MAYÚS izquierda|
|VK_MEDIA_NEXT_TRACK|Windows: Tecla pista siguiente|
|VK_MEDIA_PLAY_PAUSE|Windows: Tecla Reproducir/pausar medio|
|VK_MEDIA_PREV_TRACK|Windows: Tecla pista anterior|
|VK_MEDIA_STOP|Windows: Tecla multimedia detener|
|VK_MODECHANGE|Solicitud de cambio del modo IME|
|VK_NONCONVERT|No conversión IME|
|VK_OEM_1|Windows: Para el teclado estándar de Estados Unidos, la ';:' clave|
|VK_OEM_102|Windows: La tecla de corchete angular de cierre o la tecla de barra diagonal inversa en el teclado de 102 teclas RT|
|VK_OEM_2|Windows: ¿Para el teclado estándar de Estados Unidos, la '/'? key|
|VK_OEM_3|Windows: Para el teclado estándar de Estados Unidos, la '' ~' clave|
|VK_OEM_4|Windows: Para el teclado estándar de Estados Unidos, la ' [{"clave|
|VK_OEM_5|Windows: Para el teclado estándar de Estados Unidos, la '\\&#124;' clave|
|VK_OEM_6|Windows: Para el teclado estándar de Estados Unidos, la ']}' clave|
|VK_OEM_7|Windows: Para el teclado estándar de Estados Unidos, la tecla ' comilla/double-comilla'|
|VK_OEM_COMMA|Windows: Para cualquier país o región, la tecla ''|
|VK_OEM_MINUS|Windows: Para cualquier país o región, la '-' clave|
|VK_OEM_PERIOD|Windows: Para cualquier país o región, la '.' clave|
|VK_OEM_PLUS|Windows: Para cualquier país o región, la tecla '+'|
|VK_PACKET|Windows: Se usa para pasar caracteres Unicode como si fueran pulsaciones de teclas.|
|VK_RCONTROL|Tecla CONTROL derecha|
|VK_RMENU|Tecla MENÚ derecha|
|VK_RSHIFT|Tecla MAYÚS derecha|
|VK_SLEEP|Tecla Equipo suspendido|
|VK_VOLUME_DOWN|Windows: Tecla Bajar volumen|
|VK_VOLUME_MUTE|Windows: Tecla Silenciar volumen|
|VK_VOLUME_UP|Windows: Tecla Subir volumen|
|VK_XBUTTON1|Windows: Botón del mouse X1|
|VK_XBUTTON2|Windows: Botón del mouse X2|

## <a name="associating-an-accelerator-key-with-a-menu-item"></a>Asociar una tecla de aceleración a un elemento de menú

Muchas veces se desea que un elemento de menú y una combinación de teclado ejecuten el mismo comando de programa. Para hacerlo, asigne el mismo identificador (Id.) de recurso al elemento de menú y a una entrada de la tabla de aceleradores de la aplicación. A continuación, edite el título del elemento de menú para que muestre el nombre del acelerador. Para obtener más información sobre los elementos de menú y las teclas de aceleración, vea [asociar una tecla de aceleración a un elemento de menú](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de aceleradores](../windows/accelerator-editor.md)<br/>
[Editores de recursos](../windows/resource-editors.md)
