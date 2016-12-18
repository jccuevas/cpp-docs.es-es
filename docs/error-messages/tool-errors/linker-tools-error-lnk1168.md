---
title: "Error de las herramientas del vinculador LNK1168 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1168"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1168"
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1168
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir 'nombredearchivo' para escritura  
  
 El vinculador no puede escribir en `filename`.  El archivo puede estar en uso y el identificador de archivo puede estar bloqueado por otro proceso, o puede que no tenga permiso de escritura en el archivo, el directorio o el recurso compartido de red en que se encuentra.  Este error suele causarlo una condición transitoria, por ejemplo, un bloqueo de un programa antivirus, un proceso de indización de búsqueda de archivos o un retraso al liberar un bloqueo realizado del sistema de compilación de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Para solucionar este problema, compruebe que el identificador de archivos de `filename` no está bloqueado y que tiene permiso de escritura en el archivo.  Si es un archivo ejecutable, asegúrese de que no está en ejecución.  
  
 Puede usar las utilidades de Windows SysInternals [Handle](http://technet.microsoft.com/sysinternals/bb896655.aspx) o [Process Explorer](http://technet.microsoft.com/sysinternals/bb896653) para determinar qué proceso tiene un bloqueo de identificador de archivo en `filename`.  También puede usar Process Explorer para liberar bloqueos en identificadores de archivo abiertos.  Para obtener información sobre el uso de estas herramientas, vea los archivos de Ayuda que se incluyen con ellas.  
  
 Si el archivo está bloqueado por un programa antivirus, puede solucionar este problema excluyendo los directorios de salida de compilación de la detección automática del programa antivirus.  La detección de los programas antivirus a menudo se activa por la creación de nuevos archivos en el sistema de archivos y mantiene bloqueos en los archivos mientras se ejecuta el análisis.  Consulte en la documentación del programa antivirus los detalles acerca de cómo excluir directorios específicos del análisis.  
  
 Si el archivo está bloqueado por un servicio de indización de búsqueda, puede solucionar este problema excluyendo los directorios de salida de compilación de la indización automática.  Consulte la documentación del servicio de indización para obtener más información.  Para cambiar el servicio de indización de búsqueda de Windows, utilice las **Opciones de indización** del **Panel de control** de Windows.  Para obtener más información, consulte [Mejorar las búsquedas de Windows mediante el índice: preguntas más frecuentes](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Si el proceso de compilación no puede sobrescribir el archivo ejecutable, es posible que esté bloqueado por el Explorador de archivos.  Si se ha deshabilitado el servicio **Experiencia con aplicaciones**, el Explorador de archivos puede bloquear el identificador de un archivo ejecutable durante un largo período.  Para corregir este problema, ejecute **services.msc** y abra el cuadro de diálogo **Propiedades** del servicio **Experiencia con aplicaciones**.  Cambie el valor de **Tipo de inicio** de **Deshabilitado** a **Manual**.  
  
## Vea también  
 [Puede aparecer el mensaje de error "PRJ0008" o "Error irrecuperable LNK1168" al intentar compilar una solución o un proyecto de ActiveX en Visual C\+\+](http://support.microsoft.com/kb/308358)