---
title: Crear un recurso de datos o personalizado nuevo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c82e41544bde9cdd945e23f4ea5884e4e76ae22b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871837"
---
# <a name="creating-a-new-custom-or-data-resource"></a>Crear un nuevo recurso personalizado o recurso de datos
Para crear un nuevo recurso personalizado o de datos, coloque el recurso en un archivo independiente con sintaxis de archivo de script de recursos (.rc) normal y luego incluya ese archivo haciendo clic con el botón secundario en el proyecto en el Explorador de soluciones y haciendo clic en **Archivos de inclusión de recursos** en el menú contextual.  
  
### <a name="to-create-a-new-custom-or-data-resource"></a>Para crear un nuevo recurso personalizado o de datos  
  
1. [Cree un archivo .rc](../windows/how-to-create-a-resource-script-file.md) que contenga el recurso personalizado o de datos.  
  
     Puede escribir datos personalizados en un archivo .rc como cadenas entre comillas terminadas en null o como enteros en formato octal, hexadecimal o decimal.  
  
2.  Enel **Explorador de soluciones**, haga clic con el botón secundario en el archivo .rc del proyecto y luego haga clic en **Archivos de inclusión de recursos** en el menú contextual.  
  
3.  En el cuadro **Directivas de tiempo de compilación** escriba una instrucción **#include** que ofrece el nombre del archivo que contiene el recurso personalizado. Por ejemplo:  
  
 ```  
    #include mydata.rc  
 ```  
  
     Asegúrese de que la sintaxis y la ortografía de lo que escribe son correctas. El contenido del cuadro **Directivas de tiempo de compilación** se insertan en el archivo de script de recursos exactamente como lo escribió.  
  
4.  Haga clic en **Aceptar** para registrar sus cambios.  
  
 Otra forma de crear un recurso personalizado es importar un archivo externo como recurso personalizado. Para más información, vea [Importación y exportación de recursos](../windows/how-to-import-and-export-resources.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Binary Editor](binary-editor.md)

