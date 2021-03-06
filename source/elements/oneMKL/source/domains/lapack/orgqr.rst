.. _onemkl_lapack_orgqr:

onemkl::lapack::orgqr
=====================


.. container::


   Generates the real orthogonal matrix Q of the QR factorization formed
   by geqrf.


      ``orgqr`` supports the following precisions.


      .. list-table:: 
         :header-rows: 1

         * -  T 
         * -  ``float`` 
         * -  ``double`` 




.. container:: section


   .. rubric:: Description
      :class: sectiontitle


   The routine generates the whole or part of ``m``-by-``m`` orthogonal
   matrix ``Q`` of the ``QR`` factorization formed by the routine
   :ref:`onemkl_lapack_geqrf`.


   Usually ``Q`` is determined from the ``QR`` factorization of an ``m``
   by ``p`` matrix ``A`` with ``m≥p``. To compute the whole matrix
   ``Q``, use:


   ::


      onemkl::orgqr(queue, m, m, p, a, lda, tau, scratchpad, scratchpad_size)


   To compute the leading ``p`` columns of ``Q`` (which form an
   orthonormal basis in the space spanned by the columns of ``A``):


   ::


      onemkl::orgqr(queue, m, p, p, a, lda, tau, scratchpad, scratchpad_size)


   To compute the matrix ``Q``\ :sup:`k` of the ``QR`` factorization of
   leading ``k`` columns of the matrix ``A``:


   ::


      onemkl::orgqr(queue, m, m, k, a, lda, tau, scratchpad, scratchpad_size)


   To compute the leading ``k`` columns of ``Q``\ :sup:`k` (which form
   an orthonormal basis in the space spanned by leading ``k`` columns of
   the matrix ``A``):


   ::


      onemkl::orgqr(queue, m, k, k, a, lda, tau, scratchpad, scratchpad_size)


onemkl::lapack::orgqr (BUFFER Version)
--------------------------------------

.. container::

   .. container:: section


      .. rubric:: Syntax
         :class: sectiontitle


      .. cpp:function::  void onemkl::lapack::orgqr(cl::sycl::queue &queue, std::int64_t m,      std::int64_t n, std::int64_t k, cl::sycl::buffer<T,1> &a, std::int64_t lda,      cl::sycl::buffer<T,1> &tau, cl::sycl::buffer<T,1> &scratchpad, std::int64_t scratchpad_size)

.. container:: section


   .. rubric:: Input Parameters
      :class: sectiontitle


   queue
      The queue where the routine should be executed.


   m
      The number of rows in the matrix ``A`` (``0≤m``).


   n
      The number of columns in the matrix ``A`` (``0≤n``).


   k
      The number of elementary reflectors whose product defines the
      matrix ``Q`` (``0≤k≤n``).


   a
      The buffer ``a`` as returned by
      :ref:`onemkl_lapack_geqrf`.


   lda
      The leading dimension of a (``lda≤m``).


   tau
      The buffer ``tau`` as returned by
      :ref:`onemkl_lapack_geqrf`.


   scratchpad_size
      Size of scratchpad memory as a number of floating point elements of type T.
      Size should not be less than the value returned by :ref:`onemkl_lapack_orgqr_scratchpad_size` function.


.. container:: section


   .. rubric:: Output Parameters
      :class: sectiontitle


   a
      Overwritten by n leading columns of the m-by-m orthogonal matrix
      ``Q``.


   scratchpad
      Buffer holding scratchpad memory to be used by routine for storing intermediate results.


   .. container:: section


      .. rubric:: Throws
         :class: sectiontitle


      onemkl::lapack::exception
         Exception is thrown in case of problems happened during calculations. The ``info`` code of the problem can be obtained by `get_info()` method of exception object:

         If ``info=-i``, the ``i``-th parameter had an illegal value.

         If ``info`` equals to value passed as scratchpad size, and ``get_detail()`` returns non zero, then passed scratchpad is of insufficient size, and required size should not be less than value return by ``get_detail()`` method of exception object.


onemkl::lapack::orgqr (USM Version)
--------------------------------------

.. container::

   .. container:: section


      .. rubric:: Syntax
         :class: sectiontitle


      .. cpp:function::  cl::sycl::event onemkl::lapack::orgqr(cl::sycl::queue &queue, std::int64_t m,      std::int64_t n, std::int64_t k, T *a, std::int64_t lda,      T *tau, T *scratchpad, std::int64_t scratchpad_size, const cl::sycl::vector_class<cl::sycl::event> &events = {})

.. container:: section


   .. rubric:: Input Parameters
      :class: sectiontitle


   queue
      The queue where the routine should be executed.


   m
      The number of rows in the matrix ``A`` (``0≤m``).


   n
      The number of columns in the matrix ``A`` (``0≤n``).


   k
      The number of elementary reflectors whose product defines the
      matrix ``Q`` (``0≤k≤n``).


   a
      The pointer to ``a`` as returned by
      :ref:`onemkl_lapack_geqrf`.


   lda
      The leading dimension of a (``lda≤m``).


   tau
      The pointer to ``tau`` as returned by
      :ref:`onemkl_lapack_geqrf`.


   scratchpad_size
      Size of scratchpad memory as a number of floating point elements of type T.
      Size should not be less than the value returned by :ref:`onemkl_lapack_orgqr_scratchpad_size` function.

   events
      List of events to wait for before starting computation. Defaults to empty list.


.. container:: section


   .. rubric:: Output Parameters
      :class: sectiontitle


   a
      Overwritten by n leading columns of the m-by-m orthogonal matrix
      ``Q``.


   scratchpad
      Pointer to scratchpad memory to be used by routine for storing intermediate results.


   .. container:: section


      .. rubric:: Throws
         :class: sectiontitle


      onemkl::lapack::exception
         Exception is thrown in case of problems happened during calculations. The ``info`` code of the problem can be obtained by `get_info()` method of exception object:

         If ``info=-i``, the ``i``-th parameter had an illegal value.

         If ``info`` equals to value passed as scratchpad size, and ``get_detail()`` returns non zero, then passed scratchpad is of insufficient size, and required size should not be less than value return by ``get_detail()`` method of exception object.


   .. container:: section


      .. rubric:: Return Values
         :class: sectiontitle


      Output event to wait on to ensure computation is complete.


.. container:: familylinks


   .. container:: parentlink


      **Parent topic:** :ref:`onemkl_lapack-linear-equation-routines` 


