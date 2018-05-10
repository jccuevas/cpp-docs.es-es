---
title: 'Cómo: agregar compatibilidad con MFC a archivos de Script de recursos | Documentos de Microsoft'
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
ms.openlocfilehash: 50c0493e630c2b141da1fced6964ffc514c761d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Cómo: Agregar compatibilidad con MFC a los archivos de script de recursos
Normalmente, cuando se compila una aplicación MFC para Windows con el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), el asistente genera un conjunto básico de archivos (incluido un archivo de recursos (.rc) de la secuencia de comandos) que contiene las características principales de Microsoft Foundation clases (MFC). Sin embargo, cuando se edita un archivo .rc para una aplicación Windows que no esté basada en MFC, no estarán disponibles las siguientes características, específicas del marco de trabajo de MFC:  
  
-   Asistentes para código MFC (anteriormente denominados "[MFC ClassWizard](http://msdn.microsoft.com/en-us/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
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
    >  Además de tener que establecer este marcador, el archivo .rc deberá formar parte de un proyecto MFC. Por ejemplo, sólo se establece **MFC Mode** a **True** en un archivo .rc de Win32 proyecto no obtendrá ninguna de las características MFC.  
  

  
 **Requisitos**  
  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)