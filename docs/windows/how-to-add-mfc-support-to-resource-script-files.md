---
title: 'Cómo: agregar compatibilidad con MFC a archivos de Script de recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7237366daeaa71ba423aa069bb634b1b9f6bc667
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569747"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Cómo: Agregar compatibilidad con MFC a los archivos de script de recursos
Normalmente, cuando crea una aplicación MFC para Windows usando el [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos (como un archivo de recursos (.rc) de la secuencia de comandos) que contiene las características principales de Microsoft Foundation clases (MFC). Sin embargo, cuando se edita un archivo .rc para una aplicación Windows que no esté basada en MFC, no estarán disponibles las siguientes características, específicas del marco de trabajo de MFC:  
  
-   Los asistentes para código MFC (denominada anteriormente "[MFC ClassWizard](http://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
-   Cadenas de mensajes de menú  
  
-   Contenidos de listas de controles de cuadro combinado  
  
-   Hospedaje de controles ActiveX  
  
 No obstante, es posible agregar compatibilidad con MFC a archivos .rc que no la tengan.  
  
### <a name="to-add-mfc-support-to-rc-files"></a>Para agregar compatibilidad con MFC a archivos .rc  
  
1.  Abra el archivo de script de recursos.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En [vista de recursos](../windows/resource-view-window.md), resalte la carpeta de recursos (por ejemplo, MFC.rc).  
  
3.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), establezca el **MFC Mode** propiedad **True**.  
  
    > [!NOTE]
    >  Además de tener que establecer este marcador, el archivo .rc deberá formar parte de un proyecto MFC. Por ejemplo, simplemente establecer **MFC Mode** a **True** en un archivo .rc en Win32 proyecto no obtendrá ninguna de las características MFC.  
  
## <a name="requirements"></a>Requisitos  
  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)