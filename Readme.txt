//portfolio section dynamic data php (not working)



<!-- ======= Portfolio Section ======= -->
<section id="portfolio" class="portfolio">
  <div class="container">

    <div class="section-title">
      <h2>Portfolio</h2>
      <p>My Works</p>
    </div>

    <div class="row">
      <div class="col-lg-12 d-flex justify-content-center">
        <ul id="portfolio-flters">
          <li data-filter="*" class="filter-active">All</li>
          <?php
            $cat_list = "SELECT * FROM `category`";
            $cat_result = mysqli_query($con, $cat_list);
            if($cat_result -> num_rows > 0){
              while($cat_data = $cat_result -> fetch_assoc()){
                ?>
                <li data-filter=".<?php echo $cat_data['name']?>"><?php echo $cat_data['name']?></li>
                <?php
              }
            }
          ?>
        </ul>
      </div>
    </div>

    <div class="row portfolio-container">
   <?php
        $portfolio = "SELECT * FROM `portfolio`";
        $portfolio_result = mysqli_query($con, $portfolio);
            $category = $portfolio_data['category'];
              $category_sql = "SELECT * FROM `category` WHERE `category`.`id`='$category'";
              $category_result = mysqli_query($con, $category_sql);
              $category_data = mysqli_fetch_assoc($category_result);
            ?>
              <div class="col-lg-4 col-md-6 portfolio-item <?=$category_data['name']?>">
                <div class="portfolio-wrap">
                  <img src="<?=$portfolio_data['image']?>" class="img-fluid" alt="">
                  <div class="portfolio-info">
                    <h4><?=$portfolio_data['title']?></h4>
                    <p><?=$category_data['name']?></p>
                    <div class="portfolio-links">
                      <a href="<?=$portfolio_data['image']?>" data-gallery="portfolioGallery" class="portfolio-lightbox" title="<?php echo $portfolio_data['title']?>"><i class="bx bx-plus"></i></a>
                      <a href="portfolio-details.php?id=<?php echo $portfolio_data['id']?>" data-gallery="portfolioDetailsGallery" data-glightbox="type: external" class="portfolio-details-lightbox" title="Portfolio Details"><i class="bx bx-link"></i></a>
                    </div>
                  </div>
                </div>
              </div>
            <?php
      ?>
    </div>

  </div>
</section><!-- End Portfolio Section -->

















