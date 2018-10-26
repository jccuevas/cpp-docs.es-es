---
title: Probar el proveedor de sólo lectura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 309dc98988e4ae4fb1edd75bfb303fc8d9b078cd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059147"
---
# <a name="testing-the-read-only-provider"></a>Probar el proveedor de sólo lectura

Para probar un proveedor, se necesita un consumidor. Resulta útil si el consumidor puede contrastar con el proveedor. Las plantillas de consumidor OLE DB son un contenedor fino alrededor de OLE DB y coinciden con los objetos COM del proveedor. Dado que el origen se incluye con las plantillas de consumidor, es fácil de depurar un proveedor con ellos. Las plantillas de consumidor también son una manera muy pequeña y rápida para desarrollar aplicaciones de consumidor.

El ejemplo de este tema crea una aplicación de MFC Application Wizard predeterminada para un consumidor de prueba. La aplicación de prueba es un cuadro de diálogo sencillo con código de plantilla de consumidor OLE DB agregado.

## <a name="to-create-the-test-application"></a>Para crear la aplicación de prueba

1. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

1. En el **tipos de proyecto** panel, seleccione el **proyectos de Visual C++** carpeta. En el **plantillas** panel, seleccione **aplicación MFC**.

1. Escriba el nombre del proyecto, *TestProv*y, a continuación, haga clic en **Aceptar**.

   Aparece el Asistente para aplicaciones MFC.

1. En el **tipo de aplicación** página, seleccione **en función del cuadro de diálogo**.

1. En el **características avanzadas** página, seleccione **automatización**y, a continuación, haga clic en **finalizar**.

> [!NOTE]
> La aplicación no requiere compatibilidad de automatización si agrega `CoInitialize` en `CTestProvApp::InitInstance`.

Puede ver y editar la **TestProv** cuadro de diálogo (IDD_TESTPROV_DIALOG) si lo selecciona en **vista de recursos**. Coloque dos cuadros de lista, uno para cada cadena en el conjunto de filas, en el cuadro de diálogo. Desactivar la propiedad de ordenación para los cuadros de lista presionando **Alt**+**ENTRAR** cuando se selecciona un cuadro de lista, haga clic en el **estilos** pestaña y borrar el  **Ordenación** casilla de verificación. Además, coloque un **ejecutar** botón en el cuadro de diálogo para buscar el archivo. El terminado **TestProv** cuadro de diálogo debe tener dos cuadros de lista con la etiqueta "String 1" y "String 2", respectivamente; también tiene **Aceptar**, **cancelar**, y **ejecutar**  botones.

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

El código representa un registro de usuario que define qué columnas estarán en el conjunto de filas. Cuando el cliente llama a `IAccessor::CreateAccessor`, utiliza estas entradas para especificar las columnas que se va a enlazar. Las plantillas de consumidor OLE DB también le permiten enlazar columnas dinámicamente. Las macros COLUMN_ENTRY son la versión de cliente de las macros PROVIDER_COLUMN_ENTRY. Las dos macros COLUMN_ENTRY especifican el ordinal, tipo, longitud y miembro de datos para las dos cadenas.

Agregar una función de controlador para el **ejecutar** botón presionando **Ctrl** y haga doble clic en el **ejecutar** botón. Coloque el código siguiente en la función:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CtestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
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

El `CCommand`, `CDataSource`, y `CSession` clases todos pertenecen a las plantillas de consumidor OLE DB. Cada clase emula un objeto COM en el proveedor. El `CCommand` objeto toma la `CProvider` (clase), declarado en el archivo de encabezado, como un parámetro de plantilla. El `CProvider` parámetro representa los enlaces que utilizan para tener acceso a los datos del proveedor. Este es el `Open` código para el origen de datos, la sesión y el comando:

```cpp
if (source.Open("Custom.Custom.1", NULL) != S_OK)
   return;

if (session.Open(source) != S_OK)
   return;

if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
   return;
```

Las líneas para abrir cada una de las clases crean cada objeto COM en el proveedor. Para buscar el proveedor, utilice el `ProgID` del proveedor. Puede obtener el `ProgID` desde el registro del sistema o mediante una búsqueda en el archivo Custom.rgs (abra el directorio del proveedor y busque la `ProgID` clave).

Se incluye con el archivo MyData.txt el `MyProv` ejemplo. Para crear un archivo de su elección, use un editor y escriba un número par de cadenas, presionando ENTRAR entre cada cadena. Cambie el nombre de ruta de acceso si mueve el archivo.

Pase la cadena "c:\\\samples\\\myprov\\\MyData.txt" en el `table.Open` línea. Si va a la `Open` llamada, verá que esta cadena se pasa a la `SetCommandText` método del proveedor. Tenga en cuenta que el `ICommandText::Execute` método utiliza esa cadena.

Para capturar los datos, llame a `MoveNext` en la tabla. `MoveNext` las llamadas del `IRowset::GetNextRows`, `GetRowCount`, y `GetData` funciones. Cuando no hay más filas (es decir, es mayor que la posición actual en el conjunto de filas `GetRowCount`), el bucle finaliza:

```cpp
while (table.MoveNext() == S_OK)
{
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

Tenga en cuenta que cuando no hay más filas, los proveedores devolverán DB_S_ENDOFROWSET. El valor DB_S_ENDOFROWSET no es un error. Siempre debe comprobar con S_OK para cancelar un bucle de recopilación de datos y no utilizar la macro SUCCEEDED.

Ahora podrá compilar y probar el programa.

## <a name="see-also"></a>Vea también

[Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)