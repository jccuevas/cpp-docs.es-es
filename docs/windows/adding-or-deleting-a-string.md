---
title: Adición o eliminación de una cadena | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e15e29c99dba89ef29ba5b909c62f819bedf63f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858762"
---
# <a name="adding-or-deleting-a-string"></a>Agregar o eliminar una cadena
Puede insertar rápidamente las nuevas entradas en la tabla de cadenas con el editor de cadenas. Nuevas cadenas se colocan al final de la tabla y tienen el siguiente identificador disponible. A continuación, puede editar las propiedades ID, Value o Caption en la [ventana propiedades](/visualstudio/ide/reference/properties-window) según sea necesario.  
  
 El editor de cadenas se asegura de que no use un identificador que ya está en uso. Si selecciona un identificador ya en uso, el editor de cadenas se notificará y, a continuación, asignar un identificador genérico único, por ejemplo IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Para agregar una entrada de tabla de cadena  
  
1.  Abra la tabla de cadenas haciendo doble clic en su icono en [vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Doble clic en la tabla de cadenas y elija **nueva cadena** en el menú contextual.  
  
3.  En el **cadena** editor, seleccione una **ID** en la lista de identificadores de lista desplegable o escribir una directamente en contexto de identificador.  
  
4.  Editar la **valor**, si es necesario.  
  
5.  Escriba una entrada para el **título**.  
  
    > [!NOTE]
    >  No se permiten cadenas nulas en tablas de cadenas de Windows. Si crea una entrada en la tabla de cadenas es una cadena nula, recibirá un mensaje pidiéndole que "Especifique una cadena para esta entrada de tabla".  
  
### <a name="to-delete-a-string-table-entry"></a>Para eliminar una entrada de tabla de cadenas  
  
1.  Seleccione la entrada que quiera eliminar.  
  
2.  En el **editar** menú, haga clic en **eliminar**.  
  
 \- o -  
  
-   Haga clic en la cadena que desea eliminar y elija **eliminar** en el menú contextual.  
  
 \- o -  
  
-   Presione el **eliminar** clave.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* . Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de cadenas](../windows/string-editor.md)   

