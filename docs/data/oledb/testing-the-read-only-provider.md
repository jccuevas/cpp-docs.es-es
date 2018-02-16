---
title: "Probar el proveedor de sólo lectura | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fd224163f11a4ebafde8faf6b0c3156d89de1781
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="testing-the-read-only-provider"></a>Probar el proveedor de sólo lectura
Para probar un proveedor, se necesita un consumidor. Resulta útil si el consumidor puede coincide con el proveedor. Las plantillas de consumidor OLE DB son un contenedor fino alrededor de OLE DB y coinciden con los objetos COM del proveedor. Dado que el origen se incluye con las plantillas de consumidor, es fácil de depurar un proveedor con ellos. Las plantillas de consumidor también son una forma muy pequeña y rápida para desarrollar aplicaciones de consumidor.  
  
 El ejemplo de este tema, crea una aplicación de Asistente para aplicaciones MFC predeterminada para un consumidor de prueba. La aplicación de prueba es un cuadro de diálogo simple con código de plantilla de consumidor OLE DB agregado.  
  
### <a name="to-create-the-test-application"></a>Para crear la aplicación de prueba  
  
1.  En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.  
  
2.  En el panel tipos de proyecto, seleccione la **proyectos de Visual C++** carpeta. En el panel Plantillas, seleccione **aplicación MFC**.  
  
3.  Para el nombre del proyecto, escriba **TestProv**y, a continuación, haga clic en **Aceptar**.  
  
     Aparece el Asistente para aplicaciones MFC.  
  
4.  En el **tipo de aplicación** página, seleccione **diálogo según**.  
  
5.  En el **características avanzadas** página, seleccione **automatización**y, a continuación, haga clic en **finalizar**.  
  
> [!NOTE]
>  La aplicación no requiere compatibilidad con la automatización si agrega **CoInitialize** en **CTestProvApp:: InitInstance**.  
  
 Puede ver y editar el cuadro de diálogo TestProv (IDD_TESTPROV_DIALOG), selecciónelo en la vista de recursos. Coloque dos cuadros de lista, uno para cada cadena del conjunto de filas, en el cuadro de diálogo. Desactivar la propiedad de ordenación para los cuadros de lista presionando ALT + ENTRAR cuando se selecciona un cuadro de lista, haga clic en el **estilos** pestaña y borrar el **ordenación** casilla de verificación. Además, coloque un **ejecutar** botón en el cuadro de diálogo para buscar el archivo. El cuadro de diálogo finalizado de TestProv debe tener dos cuadros de lista con las etiquetas "String 1" y "String 2", respectivamente; También tiene **Aceptar**, **cancelar**, y **ejecutar** botones.  
  
 Abra el archivo de encabezado para la clase de cuadro de diálogo (en este caso, TestProvDlg.h). Agregue el código siguiente al archivo de encabezado (fuera de cualquier declaración de clase):  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
class CProvider   
{  
// Attributes  
public:  
   char   szField1[16];  
   char   szField2[16];  
  
   // Binding Maps  
BEGIN_COLUMN_MAP(CProvider)  
   COLUMN_ENTRY(1, szField1)  
   COLUMN_ENTRY(2, szField2)  
END_COLUMN_MAP()  
};  
```  
  
 El código representa un registro de usuario que define qué columnas se quedan en el conjunto de filas. Cuando el cliente llama **IAccessor:: CreateAccessor**, utiliza estas entradas para especificar las columnas que desea enlazar. Las plantillas de consumidor OLE DB también permiten enlazar columnas dinámicamente. Las macros COLUMN_ENTRY son la versión de cliente de las macros PROVIDER_COLUMN_ENTRY. Las dos macros COLUMN_ENTRY especifican el ordinal, el tipo, longitud y miembro de datos para las dos cadenas.  
  
 Agregar una función de controlador para el **ejecutar** botón presionando CTRL y haga doble clic en el **ejecutar** botón. Coloque el código siguiente en la función:  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
      return;  
  
   while (table.MoveNext() == S_OK)  
   {  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
   }  
}  
```  
  
 El `CCommand`, `CDataSource`, y `CSession` clases todas pertenecen a las plantillas de consumidor OLE DB. Cada clase emula un objeto COM en el proveedor. El `CCommand` objeto toma la `CProvider` (clase), declarado en el archivo de encabezado, como un parámetro de plantilla. El `CProvider` parámetro representa enlaces que utilizan para tener acceso a los datos del proveedor. Este es el `Open` código para el origen de datos, la sesión y el comando:  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 Las líneas para abrir cada una de las clases crean cada objeto COM en el proveedor. Para buscar el proveedor, utilice el ProgID del proveedor. Puede obtener el ProgID del registro del sistema o mediante una búsqueda en el archivo MyProvider.rgs (abra el proveedor directorio y busque la clave ProgID).  
  
 El archivo MyData.txt se incluye en el ejemplo MyProv. Para crear un archivo de su propio, utilice un editor y escriba un número par de cadenas, presione la tecla ENTRAR entre cada cadena. Cambie el nombre de ruta de acceso si mueve el archivo.  
  
 Pase la cadena "c:\\\samples\\\myprov\\\MyData.txt" en la `table.Open` línea. Si se encuentra en la `Open` llamada, verá que esta cadena se pasa a la `SetCommandText` método del proveedor. Tenga en cuenta que el `ICommandText::Execute` método utilizó esa cadena.  
  
 Para capturar los datos, llame a `MoveNext` en la tabla. `MoveNext` llamadas a la **IRowset:: GetNextRows**, `GetRowCount`, y `GetData` funciones. Cuando no haya más filas (es decir, la posición actual en el conjunto de filas es mayor que `GetRowCount`), el bucle finaliza:  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 Tenga en cuenta que cuando no haya más filas, los proveedores devolverán **DB_S_ENDOFROWSET**. El **DB_S_ENDOFROWSET** valor no es un error. Siempre debe comprobar con `S_OK` para cancelar un bucle de recopilación de datos y no utilizar la macro SUCCEEDED.  
  
 Ahora puede compilar y probar el programa.  
  
## <a name="see-also"></a>Vea también  
 [Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)