				      /*RLC Circuit */

#include<stdio.h>		//Header files
#include<math.h>
#include<stdlib.h>

void
main ()
{
  float v, r, l, c, f, i;	//Declaring variables
  float Xc, Xl, Z, Vr, Vc, Vl;
  float pi = 3.1415926535;

  printf ("Enter voltage=");
  scanf ("%f", &v);
  printf ("Enter resistance=");
  scanf ("%f", &r);
  printf ("Enter inductance=");
  scanf ("%f", &l);
  printf ("Enter capacitance=");
  scanf ("%f", &c);
  printf ("Enter frequency=");
  scanf ("%f", &f);

  Xc = (1 / (2 * pi * f * c));	//Formula to calculate the value of Capacitive Reactance

  Xl = 2 * pi * f * l;		//Formula to calculate the value of Inductive Reactance


  if (c == 0 && l == 0)
    {
      i = v / r;
      printf ("CURRENT=%f\n", i);
      Z = r;
      printf ("IMPEDANCE=%f\n", Z);
      Vr = i * r;
      printf ("VOLTAGE=%f\n ", Vr);
    }

  //Vr, Vc, Vl are voltages in RESISTOR, capacitor and Inductor respectively

  else if (l == 0)
    {
      Z = (sqrt ((r * r) + (Xc) * (Xc)));  //Formula to calculate IMPEDANCE
      printf (" IMPEDANCE =%f\n ", Z);
      i = v / Z;
      printf ("CURRENT=%f\n", i);
      Vr = i * r;
      printf ("Vr=%f\n ", Vr);
      Vc = i * Xc;
      printf ("Vc=%f\n ", Vc);

    }

  else if (c == 0)
    {
      Z = (sqrt ((r * r) + (Xl * Xl)));
      printf (" IMPEDANCE =%f\n ", Z);
      i = v / Z;
      printf ("CURRENT=%f\n", i);
      Vr = i * r;
      printf ("Vr=%f\n ", Vr);
      Vl = i * Xl;
      printf ("Vl=%f\n ", Vl);

    }
  else
    {
      Z = (sqrt ((r * r) + ((Xl - Xc) * (Xl - Xc))));
      printf ("IMPEDANCE=%f\n", Z);
      i = v / Z;
      printf ("CURRENT=%f\n", i);
      Vr = i * r;
      Vc = i * c;
      Vl = i * l;
      printf ("Vr=%f\n Vc=%f\n Vl=%f\n", Vr, Vc, Vl);
    }


  if (c == 0 && l == 0)
    {
      printf ("The circuit is pure Resistive circuit");

    }
  else if (c == 0 && r == 0)
    {
      printf ("The circuit is pure Inductive circuit");

    }
  else if (l == 0 && r == 0)
    {
      printf ("The circuit is pure capacitive circuit");

    }
  else if (c == 0)
    {
      printf ("The cicuit is R-L circuit");
    }
  else if (l == 0)
    {
      printf ("The circuit is R-C circuit");

    }
  else
    {
      printf ("The circuit is R-L-C circuit");

    }

}
