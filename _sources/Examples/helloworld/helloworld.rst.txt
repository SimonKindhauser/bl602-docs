.. _helloworld-index:

Hello World
===========

Overview
------

This project explains how to start up the board and print simple logging messages to the console.

Code Examples
-------------
Logging over the serial connection is as simple as a standard call to ``printf``. A ``log`` function could look like this:
::
    void log_step(const char *step[2])
    {
      printf("%s   %s\r\n", step[0], step[1]);
    }

The most basic functionality - a hello world - which uses our logging function could then look like this:
::
    void helloworld(void)
    {
      log_step(ci_table_step_init);
      log_step(ci_table_step_log);
      log_step(ci_table_step_end);
    }
Here the variables ``ci_table_step_*`` are defined as arrays with two fields. The declaration can be found a little further up (line 37-39) but the values are hidden away in ``demo.h``.
::
    
    void bfl_main(void)
    {
      bl_uart_init(0, 16, 7, 255, 255, 2 * 1000 * 1000);
      helloworld();
    }

The entry point for this example is ``void bfl_main(void)``. Here we configure the baud rate to 2000000bps. Run the example, and you should see ``start`` ， ``helloworld`` ， ``end`` printed to the serial console.

.. figure:: imgs/image1.png
   :alt:
