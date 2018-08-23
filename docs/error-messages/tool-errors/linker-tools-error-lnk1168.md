---
title: Las herramientas del vinculador LNK1168 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9437b88b67254a63babf5b72379a760d1ab86062
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540518"
---
# <a name="linker-tools-error-lnk1168"></a>Error de las herramientas del vinculador LNK1168
no se puede abrir 'nombredearchivo' para escritura  
  
 El vinculador no puede escribir en `filename`. El archivo puede estar en uso y el identificador de archivo puede estar bloqueado por otro proceso, o puede que no tenga permiso de escritura en el archivo, el directorio o el recurso compartido de red en que se encuentra. Este error se produce con frecuencia una condición transitoria, por ejemplo, un programa antivirus, mantiene un bloqueo de proceso de indización de búsqueda de un archivo, o un retraso al liberar un bloqueo mantenido por el sistema de compilación de Visual Studio.  
  
 Para solucionar este problema, compruebe que el identificador de archivos de `filename` no está bloqueado y que tiene permiso de escritura en el archivo. Si es un archivo ejecutable, asegúrese de que no está en ejecución.  
  
 Puede usar las utilidades de Windows SysInternals [controlar](http://technet.microsoft.com/sysinternals/bb896655.aspx) o [Process Explorer](http://technet.microsoft.com/sysinternals/bb896653) para determinar qué proceso tiene un archivo de bloqueo de identificador en `filename`. También puede usar Process Explorer para liberar bloqueos en identificadores de archivo abiertos. Para obtener información sobre el uso de estas herramientas, vea los archivos de Ayuda que se incluyen con ellas.  
  
 Si el archivo está bloqueado por un programa antivirus, puede solucionar este problema excluyendo los directorios de salida de compilación de la detección automática del programa antivirus. La detección de los programas antivirus a menudo se activa por la creación de nuevos archivos en el sistema de archivos y mantiene bloqueos en los archivos mientras se ejecuta el análisis. Consulte en la documentación del programa antivirus los detalles acerca de cómo excluir directorios específicos del análisis.  
  
 Si el archivo está bloqueado por un servicio de indización de búsqueda, puede solucionar este problema excluyendo los directorios de salida de compilación de la indización automática. Consulte la documentación del servicio de indización para obtener más información. Para cambiar el servicio de indización de búsqueda de Windows, use **opciones de indización** en el Windows **Panel de Control**. Para obtener más información, consulte [Windows mejorar las búsquedas mediante el índice: preguntas más frecuentes](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Si el proceso de compilación no puede sobrescribir el archivo ejecutable, es posible que esté bloqueado por el Explorador de archivos. Si el **aplicación experiencia** servicio se ha deshabilitado, Explorador de archivos puede contener un bloqueo del identificador de archivo ejecutable durante un período prolongado. Para solucionar este problema, ejecute **services.msc** y, a continuación, abra el **propiedades** cuadro de diálogo para la **experiencia de aplicación** service. Cambiar el **tipo de inicio** desde **deshabilitado** a **Manual**.  
  
## <a name="see-also"></a>Vea también  
 [Puede recibir un "PRJ0008" o mensaje de error "Error irrecuperable LNK1168" al intentar compilar una solución o un proyecto de ActiveX en Visual C++](http://support.microsoft.com/kb/308358)