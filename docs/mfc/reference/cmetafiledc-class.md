---
title: "CMetaFileDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMetaFileDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMetaFileDC class"
  - "metarchivos, implementar"
  - "Windows metafiles [C++]"
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 23
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMetaFileDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de \(GDI\) dispositivo gráfico que pueda volver a consultar crear una imagen deseada o texto.  
  
## Sintaxis  
  
```  
class CMetaFileDC : public CDC  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](../Topic/CMetaFileDC::CMetaFileDC.md)|Crea un objeto `CMetaFileDC`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::Close](../Topic/CMetaFileDC::Close.md)|Cierre el contexto de dispositivo y crea un identificador de metarchivo.|  
|[CMetaFileDC::CloseEnhanced](../Topic/CMetaFileDC::CloseEnhanced.md)|Cierra un contexto de dispositivo de metarchivo mejorado y crea un identificador de metarchivo mejorado.|  
|[CMetaFileDC::Create](../Topic/CMetaFileDC::Create.md)|Crea el contexto del dispositivo de metarchivo de Windows y lo asocia al objeto de `CMetaFileDC` .|  
|[CMetaFileDC::CreateEnhanced](../Topic/CMetaFileDC::CreateEnhanced.md)|Crea un contexto de dispositivo metafile para un metarchivo de ampliar\-formato.|  
  
## Comentarios  
 para implementar un metarchivo de Windows, primero cree un objeto de `CMetaFileDC` .  Invoque al constructor de `CMetaFileDC` , llame a la función miembro de [Crear](../Topic/CMetaFileDC::Create.md) , que crea un contexto de dispositivo de metarchivo de Windows y lo asocia al objeto de `CMetaFileDC` .  
  
 El Siguiente envía el objeto de `CMetaFileDC` el script de `CDC` GDI que piensa para ella reproducir.  Solo los comandos de GDI que crean la salida, como `MoveTo` y `LineTo`, pueden utilizarse.  
  
 Después de enviar los comandos que desee al metarchivo, llame a la función miembro de **Cerrar** , que cierra los contextos de dispositivo de metarchivo y devuelve un identificador de metarchivo.  A continuación se eliminan del objeto de `CMetaFileDC` .  
  
 [CDC:: PlayMetaFile](../Topic/CDC::PlayMetaFile.md) puede utilizar el identificador metafile para reproducir el metarchivo repetidamente.  El metarchivo se puede manipular también por las funciones de Windows como [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480), que copia un metarchivo en el disco.  
  
 Cuando el metarchivo ya no se necesita, elimínelo de memoria con la función de [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows.  
  
 También puede implementar el objeto de `CMetaFileDC` de modo que pueda controlar llamadas generadas y las llamadas de GDI de atributo como `GetTextExtent`.  Tal metarchivo es más flexible y resultará más fácil reutilizar el código general de GDI, que consta de a menudo una combinación de llamadas de salida y el atributo.  La clase de `CMetaFileDC` hereda dos contextos de dispositivo, `m_hDC` y `m_hAttribDC`, de `CDC`.  El contexto del dispositivo de `m_hDC` controla todas las llamadas de salida de [CDC](../../mfc/reference/cdc-class.md) GDI y el contexto del dispositivo de `m_hAttribDC` controla todas las llamadas del atributo de `CDC` GDI.  Normalmente, estos contextos de dos dispositivos hacen referencia al mismo dispositivo.  En el caso de `CMetaFileDC`, el atributo DC se establece en **NULL** de forma predeterminada.  
  
 Cree un segundo contexto de dispositivo que señale a la pantalla, a una impresora, o dispositivo distinto de un metarchivo, llame a la función miembro de `SetAttribDC` para asociar el nuevo contexto de dispositivos con `m_hAttribDC`.  Las llamadas de GDI para información ahora se tratarán a nuevo `m_hAttribDC`.  Las llamadas de GDI de salida van a `m_hDC`, que representa el metarchivo.  
  
 Para obtener más información sobre `CMetaFileDC`, vea [Contextos de dispositivo](../../mfc/device-contexts.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)