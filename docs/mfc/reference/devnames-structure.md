---
title: DEVNAMES (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 637843873bbb0e12a76168bd08b613e14b391ef8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392468"
---
# <a name="devnames-structure"></a>DEVNAMES (Estructura)

El `DEVNAMES` estructura contiene cadenas que identifican el controlador, dispositivo y los nombres de puerto de salida de una impresora.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagDEVNAMES { /* dvnm */
    WORD wDriverOffset;
    WORD wDeviceOffset;
    WORD wOutputOffset;
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */
} DEVNAMES;
```

#### <a name="parameters"></a>Parámetros

*wDriverOffset*<br/>
(Entrada/salida) Especifica el desplazamiento de caracteres en una cadena terminada en null que contiene el nombre de archivo (sin extensión) del controlador del dispositivo. En la entrada, esta cadena se usa para determinar la impresora para mostrar inicialmente en el cuadro de diálogo.

*wDeviceOffset*<br/>
(Entrada/salida) Especifica el desplazamiento de caracteres en la cadena terminada en null (máximo de 32 bytes incluir el carácter nulo) que contiene el nombre del dispositivo. Esta cadena debe ser idéntica a la `dmDeviceName` miembro de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructura.

*wOutputOffset*<br/>
(Entrada/salida) Especifica el desplazamiento de caracteres en la cadena terminada en null que contiene el nombre de dispositivo de denegación de servicio para el medio físico de salida (puerto de salida).

*wDefault*<br/>
Especifica si las cadenas que contiene el `DEVNAMES` estructura identifican la impresora predeterminada. Esta cadena se usa para comprobar que la impresora predeterminada no ha cambiado desde la última operación de impresión. En la entrada, si se establece la marca DN_DEFAULTPRN, los otros valores en el `DEVNAMES` estructura se comprueban con la impresora predeterminada actual. Si cualquiera de las cadenas no coinciden, se muestra un mensaje de advertencia que informa al usuario que deba volver a formatear el documento. En la salida, el `wDefault` miembro solo cambia si se muestra el cuadro de diálogo de instalación de impresión y el usuario elige el botón Aceptar. Si se ha seleccionado la impresora predeterminada, se establece la marca DN_DEFAULTPRN. Si se selecciona una determinada impresora, no se establece la marca. Todos los demás bits en este miembro se reservan para uso interno por el procedimiento de cuadro de diálogo de impresión.

## <a name="remarks"></a>Comentarios

El `PrintDlg` función usa estas cadenas para inicializar los miembros en el cuadro de diálogo Imprimir definido por el sistema. Cuando el usuario cierra el cuadro de diálogo, se devuelve información acerca de la impresora seleccionada en esta estructura.

## <a name="requirements"></a>Requisitos

**Encabezado:** commdlg.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


