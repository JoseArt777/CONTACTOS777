# CONTACTOS777
package com.example.contactos;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;

import androidx.appcompat.app.AppCompatActivity;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {

    ArrayList <contacto > contactos ;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        contactos= new ArrayList<contacto>();

        contactos.add(new contacto("Alex Lopez", "57388652", "lopez2@gmail.com", "Bachiller" ) ) ;
        contactos.add(new contacto("Mayda Chavez", "35672312", "chavezmayda@gmail.com", "Perito Contador" ) ) ;
        contactos.add(new contacto("Brenda Rivera", "35698741", "brenda@gmail.com", "Secretaria" ) ) ;
        contactos.add(new contacto("Enyelber Zamora", "34737803", "Zamora456@gmail.com", "amigo" ) ) ;
        contactos.add(new contacto("Anderson Cuellar", "62315482", "cuellar5789@gmail.com", "Perito Contador" ) ) ;
        contactos.add(new contacto("Cristian Urias", "78521643", "urias@gmail.com", "Bachiller" ) ) ;


        ArrayList <String>  nombresContacto=new ArrayList<>() ;
        for (contacto contacto: contactos){
                nombresContacto.add(contacto.getNombre());


        }

        ListView lstcontactos=(ListView ) findViewById(R.id.lstcontactos);
        lstcontactos .setAdapter(new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, nombresContacto   ) ) ;

    lstcontactos.setOnItemClickListener(new AdapterView.OnItemClickListener() {
        @Override
        public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
            Intent intent=new Intent(MainActivity.this, Detalle.class) ;
            intent.putExtra(getResources().getString(R.string.pnombre),contactos.get(position).getNombre() );
            intent.putExtra(getResources().getString(R.string.ptelefono),contactos.get(position).getTelefono() );
            intent.putExtra(getResources().getString(R.string.pemail),contactos.get(position).getEmail() );
            intent.putExtra(getResources().getString(R.string.pdescripcion),contactos.get(position).getDescripcion() );
            startActivity(intent) ;





        }
    });


    }
}
