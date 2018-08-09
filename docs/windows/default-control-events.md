---
title: Predeterminado de los eventos de Control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9ffea9bf6ffbbc6d34e130b2031297ff1ef3f99
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649625"
---
# <a name="default-control-events"></a>Eventos predeterminados de los controles
Los siguientes nombres de control tienen los eventos predeterminados que lo acompaña:  
  
|Nombre del control|Evento predeterminado|  
|------------------|-------------------|  
|Animate|MENSAJE ACN_START|  
|Casilla de verificación|BN_CLICKED|  
|Cuadro combinado|CBN_SELCHANGE|  
|Personalizados|NOTIFICACIÓN TTN_GETDISPINFO|  
|Selector de fecha hora|DTN_DATETIMECHANGE|  
|Cuadro de edición|EN_CHANGE|  
|Cuadro de grupo|(No aplicable)|  
|Tecla de acceso rápido|NM_OUTOFMEMORY|  
|Dirección IP|IPN_FIELDCHANGED|  
|Lista|LVN_ITEMCHANGE|  
|Cuadro de lista|LBN_SELCHANGE|  
|Calendario mensual|MCN_SELCHANGE|  
|Control de imagen|(No aplicable)|  
|Progreso|NM_CUSTOMDRAW|  
|Botón de comando|BN_CLICKED|  
|Botón de radio|BN_CLICKED|  
|Rich Edit.|EN_CHANGE|  
|Barra de desplazamiento|NM_THEMECHANGED|  
|Slider|NM_CUSTOMDRAW|  
|Número|UDN_DELTAPOS|  
|Texto estático|(No aplicable)|  
|Tab|TCN_SELCHANGE|  
|Árbol|TVN_SELCHANGE|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Definir Variables miembro para controles de cuadro de diálogo](../windows/defining-member-variables-for-dialog-controls.md)   
 [Tipos de mensajes asociados a objetos de interfaz de usuario](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [Edición de un controlador de mensajes](../mfc/reference/editing-a-message-handler.md)   
 [Definir un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [Declarar una Variable basada en la nueva clase de Control](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)