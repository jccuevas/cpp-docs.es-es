---
title: "DEVNAMES (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEVNAMES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEVNAMES"
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DEVNAMES (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `DEVNAMES` contiene las cadenas que identifican el controlador, el dispositivo, y los nombres de puerto de salida para una impresora.  
  
## Sintaxis  
  
```  
  
      typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault;  
    /* driver, device, and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### Parámetros  
 *wDriverOffset*  
 \(Entrada\) especifica el desplazamiento en caracteres en una cadena terminada en null que contiene el nombre de archivo \(sin extensión\) del controlador de dispositivo.  En la entrada, esta cadena se utiliza para determinar la impresora para mostrar inicialmente en el cuadro de diálogo.  
  
 *wDeviceOffset*  
 \(Entrada\) especifica el desplazamiento en caracteres a la cadena terminada en null \(máximo de 32 bytes incluidos null\) que contiene el nombre del dispositivo.  Esta cadena debe ser idéntica al miembro de **dmDeviceName** de la estructura de [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) .  
  
 *wOutputOffset*  
 \(Entrada\) especifica el desplazamiento en caracteres a la cadena terminada en null que contiene el nombre de dispositivo de DOS para el medio físico de salida \(puerto de salida\).  
  
 *wDefault*  
 Especifica si las cadenas incluidas en la estructura de `DEVNAMES` identifican la impresora predeterminada.  Esta cadena se utiliza para comprobar que la impresora predeterminada no ha cambiado desde la operación de impresión última.  En la salida, si se establece la marca de **DN\_DEFAULTPRN** , los otros valores en la estructura de `DEVNAMES` se comprueban con respecto a la impresora predeterminada actual.  Si no coinciden cualquiera de las cadenas, un mensaje de advertencia se muestra que informa al usuario que el documento puede necesitar cambiar el formato.  En la salida, cambian el miembro de **wDefault** sólo si el cuadro de diálogo configuración de impresión se muestra y el usuario elija el botón ACEPTAR.  Se establece la marca de **DN\_DEFAULTPRN** si la impresora predeterminada está seleccionado.  Si se selecciona una impresora concreta, el marcador no se establece.  El resto de los bits de este miembro están reservados para uso interno por el procedimiento del cuadro de diálogo imprimir.  
  
## Comentarios  
 La función de **PrintDlg** utiliza estas cadenas para inicializar los miembros en el cuadro de diálogo sistema\- definido de impresión.  Cuando el usuario cierra el cuadro de diálogo, la información sobre la impresora seleccionada se devuelve en esta estructura.  
  
## Requisitos  
 **Header:** commdlg.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)