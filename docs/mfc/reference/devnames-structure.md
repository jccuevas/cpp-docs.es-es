---
title: Estructura DEVNAMES | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 698a338c94dfa402dd51fa4f683b92a5d30cc0cd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="devnames-structure"></a>DEVNAMES (Estructura)
El `DEVNAMES` estructura contiene cadenas que identifican el controlador, el dispositivo y los nombres de puerto de salida de una impresora.  
  
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
 (Entrada/salida) Especifica el desplazamiento de caracteres en una cadena terminada en null que contiene el nombre de archivo (sin extensión) del controlador de dispositivo. En la entrada, esta cadena se usa para determinar la impresora para mostrar inicialmente en el cuadro de diálogo.  
  
 *wDeviceOffset*  
 (Entrada/salida) Especifica el desplazamiento de caracteres a la cadena terminada en null (un máximo de 32 bytes incluido el carácter null) que contiene el nombre del dispositivo. Esta cadena debe ser idéntica a la **dmDeviceName** miembro de la [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) estructura.  
  
 *wOutputOffset*  
 (Entrada/salida) Especifica el desplazamiento de caracteres a la cadena terminada en null que contiene el nombre de dispositivo de DOS para el medio físico de salida (puerto de salida).  
  
 *wDefault*  
 Especifica si las cadenas contenidas en el `DEVNAMES` estructura identifican la impresora predeterminada. Esta cadena se usa para comprobar que la impresora predeterminada no ha cambiado desde la última operación de impresión. En la entrada, si la **DN_DEFAULTPRN** establecido, los demás valores el `DEVNAMES` estructura se comprueban con la impresora predeterminada actual. Si cualquiera de las cadenas no coinciden, se muestra un mensaje de advertencia que informa al usuario que se deba volver a formatear el documento. En la salida, la **wDefault** miembro solo cambia si se muestra el cuadro de diálogo Configuración de impresora y el usuario elige el botón Aceptar. El **DN_DEFAULTPRN** marca se establece si se ha seleccionado la impresora predeterminada. Si se selecciona una impresora determinada, no se estableció el marcador. Todos los demás bits este miembro se reservan para uso interno por el procedimiento de cuadro de diálogo Imprimir.  
  
## <a name="remarks"></a>Comentarios  
 El **PrintDlg** función usa estas cadenas para inicializar los miembros en el cuadro de diálogo de impresión definida por el sistema. Cuando el usuario cierra el cuadro de diálogo, se devuelve información sobre la impresora seleccionada en esta estructura.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** commdlg.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)



