# Customizing controller actions

If you want to create more complex application behavior for a dashboard,
feel free to overwrite controller actions:

```bash
rails generate administrate:controller customer
```

... will generate `app/controllers/admin/customers_controller.rb`:

```ruby
# app/controllers/admin/customers_controller.rb

class Admin::CustomersController < Admin::DashboardController
  # Overwrite any of the RESTful controller actions to implement custom behavior
  # For example, you may want to update a customer's subscription amount
  # after they change their subscription:
  #
  # def update
  #   customer = Customer.find(params[:id])
  #   new_subscription = params[:customer][:subsciption]
  #
  #   if(new_subscription != customer.subscription)
  #     PaymentGateway.update_subsciption(customer, new_subscription) &&
  #       customer.update(permitted_customer_params)
  #   end
  # end
end
```

For complete flexibility, pair custom controllers with custom page views.
At that level of customization, Administrate becomes transparent.
there's no difference between an admin controller/view pair
and any other controller/view pair in your application.