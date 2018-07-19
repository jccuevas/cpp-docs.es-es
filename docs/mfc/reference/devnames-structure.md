---
title: DEVNAMES (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: 0c13167c42c6acbfcc5f3af500205eed6ab884d9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121580"
---
# <a name="devnames-structure"></a>DEVNAMES (Estructura)
El `DEVNAMES` estructura contiene las cadenas que identifican el controlador, el dispositivo y los nombres de puerto de salida de una impresora.  
  
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
 *wDriverOffset*  
 (Entrada/salida) Especifica el desplazamiento de caracteres en una cadena terminada en null que contiene el nombre de archivo (sin extensión) del controlador del dispositivo. En la entrada, esta cadena se usa para determinar la impresora para mostrar inicialmente en el cuadro de diálogo.  
  
 *wDeviceOffset*  
 (Entrada/salida) Especifica el desplazamiento de caracteres a la cadena terminada en null (máximo de 32 bytes incluido el carácter null) que contiene el nombre del dispositivo. Esta cadena debe ser idéntica a la `dmDeviceName` miembro de la [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) estructura.  
  
 *wOutputOffset*  
 (Entrada/salida) Especifica el desplazamiento de caracteres a la cadena terminada en null que contiene el nombre de dispositivo de DOS para el medio físico de salida (puerto de salida).  
  
 *wDefault*  
 Especifica si las cadenas se incluye en el `DEVNAMES` estructura identifican la impresora predeterminada. Esta cadena se usa para comprobar que la impresora predeterminada no ha cambiado desde la última operación de impresión. En la entrada, si se establece la marca DN_DEFAULTPRN, los otros valores en la `DEVNAMES` estructura se comprueban en la impresora predeterminada actual. Si cualquiera de las cadenas no coinciden, se muestra un mensaje de advertencia que informa al usuario que el documento que deba cambiar el formato. En la salida, la `wDefault` miembro solo cambia si se muestra el cuadro de diálogo de instalación de impresión y el usuario elige el botón Aceptar. Si se ha seleccionado la impresora predeterminada, se establece la marca DN_DEFAULTPRN. Si se selecciona una impresora determinada, no se estableció el marcador. Todos los demás bits en este miembro se reservan para uso interno por el procedimiento de cuadro de diálogo de impresión.  
  
## <a name="remarks"></a>Comentarios  
 El `PrintDlg` función estas cadenas utiliza para inicializar los miembros en el cuadro de diálogo de impresión definida por el sistema. Cuando el usuario cierra el cuadro de diálogo, se devuelve información acerca de la impresora seleccionada en esta estructura.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** commdlg.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


